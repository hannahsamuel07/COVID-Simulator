# COVID-19 Simulator
### Introduction
To have a better understanding of the usages of arrays and arraylist in Java, I experimented with switch staments and cases when I was first learning to program in Java. After a year of COVID-19 pandemic, I reflected and decided to create a simple simulation of COVID-19. This project allowed me to learn how to use array list and their application when writing code. By completeing this lab, I now have a better understanding of how to use array lists to represent a real world scenario. 

### Code Implementation
In this lab, I dealt with cell object that were contained in an arraly list. Then I created a method to detect when a cells is colliding with another cell object. This information could then be used switch between different cases. Case 1 represents a healthy status of a cell. Case 1 cells are green and cannot infect each other even when they collide with eacher because they are all healthy. The human user can click in the simulation and add yellow cells. These cells has just gotten infected with a disease and therefore go and infect other healthy cells by moving around and colliding with them. When a vaccine or antibiotic substnace is developed , for example, the COVID-19 vaccine,the patient will eventually get vaccinated. The body builds immunity which is represented with the blue cells that eventually learn how to fight the disease. When blue cells collide with infected cells objects, the swith cases change assuring that 97% of the time, the immunity gets rids of any infected cells. But there's is alwas a chance for the strain of the disease to worsen or mutate of its a virus. These cells are represented by red cell objects. This cells require a furture dose of a medical intervention. These cases are implmented through the use of switch statment that change the appearance of the cell objects under certain conditions   
```
switch(status) {
		case 0://detect when status zero
		color = Color.GREEN;
		break;
		case 1://detect when status zero
			time+=16;
		color = Color.yellow;
		if(time>5000) {
			if(Math.random()<0.97) {
				status = 2;
			}else {
				status = 3;
			}
		}
		break;	
		case 2://detect when status zero
		color = Color.blue;
		break;
		case 3://detect when status zero
			color = Color.red;
			break;
		}
	}

```
The cell objects update there position with some relationship to their velocity and acceleration  that is relative to their position
```
vy += ay;
		x+=vx;
		y+=vy;
		g.setColor(color);
		g.fillOval(x, y, width, width);
		  if(y>= 550) {
			  vy *=-1;
		  }
		  if(y<= 10) {
			  vy*=-1;
		  }
		  if(x>=750) {
			  vx*=-1;
		  }
		  if(x<=10) {
			  vx*=-1;
		  }
 ```
The collide method is the central driver of the simulation. Its checking the contact of cell objects with other cell objects changing the status to an appropriate case based on the interaction of the cell objects
```
	//returns true if this Cell is colliding with the other Cell object
		
		int x1 = this.x+width/2; //center pointx
		int y1 = this.y+width/2;
		
		//other cell center point
		int x2 = other.x+other.width/2;
		int y2 = other.y+other.width/2;
		
		int d = (int)(Math.sqrt(Math.pow(x1-x2,2)+Math.pow(y1-y2,2)));
		int r1 = this.width/2;
		int r2 = other.width/2;
		
		//figure out which cell is bigger
		//increment it's size somehow
		if(r1+r2 > d*3/2) {
			if(Math.random() <.7) {
			
			if(other.status ==1 && this.status ==0) {
				this.status = 1;// this cell is now infected
			}
			
			if(this.status == 0 && other.status == 1) {
				other.status = 1; //other cell is infected
			}
			
			if(this.area > other.area) {
				//add other area to this area
				this.area += other.area; //eat other cell			
				//calculate new width based on new area
				int r = (int)(Math.sqrt(this.area/Math.PI));
				int oldWidth = width;
				this.width = r*2;
				this.x -= (this.width-oldWidth)/2;
				this.y -= (this.width-oldWidth)/2;
				
				other.reset();
				
			}else if(this.area < other.area) {
				//add other area to this area
				other.area += this.area; //eat other cell
				//calculate new width based on new area
				int r = (int)(Math.sqrt(other.area/Math.PI));
				
				int oldWidth = other.width;
				other.width = r*2;
				other.x -= (other.width-oldWidth)/2;
				other.y -= (other.width-oldWidth)/2;
				reset();				
				
			}
		}
		
	}
		return false && (r1+r2)>d;
		
	}
  ```
### Simulation


https://user-images.githubusercontent.com/90801601/159146692-a4ec8b93-3a6d-41c4-9c5f-a863ed55636e.mp4

<hr>

