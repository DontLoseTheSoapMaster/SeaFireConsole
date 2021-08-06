import javax.swing.*; // В программе используются окна JOption Pane
import java.awt.event.*;
import java.util.*;
	class SeaFire{
		public static void main(String args[]){
			char Alphabet[] = new char[11];
			CreateAlphabet(Alphabet);
			int column[] = new int[10];
			CreateColumn(column);
			int urField[][] = new int[10][10];
			CreateField(urField);
			int enemyField[][] = new int[10][10];
			String gre = "";
			//int Direction = 0;
			CreateField(enemyField);
			int comonField[][] = new int[11][11];
			CreateField(comonField);
			int ZapretFiledUr[][] = new int[10][10];
			int ZapretFiledEnemy[][] = new int[10][10];
			int AnalyseField[][] = new int[10][10];
			CreateAnalyseField(AnalyseField, 4);
			CreateField(ZapretFiledUr);
			CreateField(ZapretFiledEnemy);
			System.out.println("Ваше Поле");
			System.out.println("");
			PrintFields(Alphabet, column, urField);
			Create4Ship(urField, ZapretFiledUr);
			PrintFields(Alphabet, column, urField);
			System.out.println("");
			System.out.println("Запретное поле игрока:");
			PrintFields(Alphabet, column, ZapretFiledUr);
			//Create4Ship(enemyField,ZapretFiledEnemy);
			CreateEnemy4Ship(enemyField,ZapretFiledEnemy);
			for(int i =0; i<2; i++){
				CreateNShip(urField,ZapretFiledUr,3);
			//	CreateNShip(enemyField,ZapretFiledEnemy,3);
				PrintFields(Alphabet, column, urField);
				System.out.println("");
				System.out.println("Запретное поле игрока:");
				PrintFields(Alphabet, column, ZapretFiledUr);
				CreateEnemyNShip(enemyField,ZapretFiledEnemy,3);
			}
			for(int i = 0; i<3; i++){
				CreateNShip(urField,ZapretFiledUr,2);
				PrintFields(Alphabet, column, urField);
				System.out.println("");
				System.out.println("Запретное поле игрока:");
				PrintFields(Alphabet, column, ZapretFiledUr);
				//CreateNShip(enemyField,ZapretFiledEnemy,2);
				CreateEnemyNShip(enemyField,ZapretFiledEnemy,2);
			}
			for(int i = 0; i<4; i++){
				CreateNShip(urField,ZapretFiledUr,1);
				PrintFields(Alphabet, column, urField);
				System.out.println("");
				System.out.println("Запретное поле игрока:");
				PrintFields(Alphabet, column, ZapretFiledUr);
				//CreateNShip(enemyField,ZapretFiledEnemy,3);
				CreateEnemyNShip(enemyField,ZapretFiledEnemy,1);
			}
			System.out.println("");
			int [] countShips = new int[]{10,10};
			PrintFields(Alphabet, column, urField, comonField,countShips);
			System.out.println("");
			System.out.println("Поле Противника");
			PrintFields(Alphabet, column, enemyField);
			JOptionPane.showMessageDialog(null, "Игра начинается! Ваш ход!", "Ваш Ход!", JOptionPane.PLAIN_MESSAGE);
			int [] MemoryQubic = new int[]{0,0,0,0,0,0,0,0,0,0,4,1,2,3,11};
			while(countShips[0] > 0 && countShips[1] > 0){
				MadeVystrel(Alphabet,column,urField,comonField, enemyField,comonField,countShips);
				if(countShips[0] > 0){
					EnemyVystrel(urField,MemoryQubic,AnalyseField,countShips);
					System.out.println("");
					PrintFields(Alphabet, column, AnalyseField);
					System.out.println("Ваше число кораблей = " + countShips[1]);
					System.out.println("число кораблей противника= " + countShips[0]);
					//System.out.println("MemoryRand[11]= " + MemoryQubic[11]);
				}
			}
			if(countShips[0] == 0){
				JOptionPane.showMessageDialog(null, "Поздравляем! Вы победили", "УИИИИИИ", JOptionPane.PLAIN_MESSAGE);
				JOptionPane.showMessageDialog(null, "*туууууууууууууууу*", "Барабанная дробь", JOptionPane.PLAIN_MESSAGE);
				JOptionPane.showMessageDialog(null, "Россия", "Россия", JOptionPane.PLAIN_MESSAGE);
				JOptionPane.showMessageDialog(null, "Священная", "Священная", JOptionPane.PLAIN_MESSAGE);
				JOptionPane.showMessageDialog(null, "Наша", "Наша", JOptionPane.PLAIN_MESSAGE);
				JOptionPane.showMessageDialog(null, "Держава", "Держава", JOptionPane.PLAIN_MESSAGE);
				JOptionPane.showMessageDialog(null, "Россия", "Россия", JOptionPane.PLAIN_MESSAGE);
				JOptionPane.showMessageDialog(null, "Все, иди домой брат, ты победил", "Дэа", JOptionPane.PLAIN_MESSAGE);
			}else{
				JOptionPane.showMessageDialog(null, "Вы проиграли", "ууууууу!", JOptionPane.PLAIN_MESSAGE);
				JOptionPane.showMessageDialog(null, "*начинают играть круутые басы*", "Бум-Бум", JOptionPane.PLAIN_MESSAGE);
				JOptionPane.showMessageDialog(null, "отпусти", "суки блять", JOptionPane.PLAIN_MESSAGE);
				JOptionPane.showMessageDialog(null, "отпусти меня", "ебать", JOptionPane.PLAIN_MESSAGE);
				JOptionPane.showMessageDialog(null, "ебучий спайс", "вот-вот же чорт", JOptionPane.PLAIN_MESSAGE);
				JOptionPane.showMessageDialog(null, "я ни", "рили", JOptionPane.PLAIN_MESSAGE);
				JOptionPane.showMessageDialog(null, "в чем", "Уххххх", JOptionPane.PLAIN_MESSAGE);
				JOptionPane.showMessageDialog(null, "не", "ахтыжепт", JOptionPane.PLAIN_MESSAGE);
				JOptionPane.showMessageDialog(null, "виноват", "да ладно?", JOptionPane.PLAIN_MESSAGE);
			}
		}
	static void CreateField(int Field1[][]){
		for(int i =0; i<10; i++){
			for(int j = 0; j<10; j++){
				Field1[i][j] = 0;
				
			}
		}
	}
	static void CreateAlphabet(char Field1[]){
		Field1[0] = 'N';
		for(int i =1; i<11; i++){
			Field1[i] = (char)(64+i);
			}
		
	}
	static void CreateColumn(int Field1[]){
		for(int i =0; i<10; i++){
			Field1[i] = i+1;
			}
		
		
	}
	static void CreateEnemy4Ship(int Field1[][], int Zap1[][]){
		int a = (int)((Math.random()) + 0.5);
		int x = (int)((Math.random())*10);
		int y = (int)((Math.random())*6);
		if(a == 1){
			int t = y;
			y = x;
			x = t;
		}
		plant4Ship(x,y,a,Field1,Zap1);
	}
	static void CreateEnemyNShip(int Field1[][], int Zap1[][], int Numer){
		int a =0;
		int x = 0;
		int y = 0;
		boolean b = false;
		boolean flag = true;
		while(b == false){
		a = (int)((Math.random()) + 0.5);
		x = (int)((Math.random())*10);
		y = (int)((Math.random())*(10-Numer));
		if(a == 1){
			int t = y;
			y = x;
			x = t;
		}
		b = ChekTheDostup(Zap1, x, y,a, Numer, Field1,flag);
		}
		plantNShip(x,y, a,Field1,Zap1,Numer);
	}
			
	static void Create4Ship(int Field1[][], int Zap1[][]){
		int a = 3;
		int x =10;
		int y = 10;
		while(a<0 || a>1){
			try{
				String v = JOptionPane.showInputDialog(null, "Расположение. 1- горизонт. 0 - вертикальное");
				char g = v.charAt(0);
				a = ((int)g)-48;
				if(a<0 || a>1){
					throw new Exception("Blet");
				}
			}catch(Exception e){
					a = 11;
					JOptionPane.showMessageDialog(null, "Вы ввели неправильные значения. Повторите операцию", "Ошибка!", JOptionPane.PLAIN_MESSAGE);
			}
		}
			while(((x<0) || (x>9)) || (a == 1 && x>6)){
				try{
					String h = JOptionPane.showInputDialog(null, "ВВедите координату x (от A до J)");
					char g = h.charAt(0);
					x = ((int)g)-65;
					if(((x<0) || (x>9)) || (a == 1 && x>6)){
						throw new Exception("Blet");
					}
				}catch(Exception e){
					x = 11;
					JOptionPane.showMessageDialog(null, "Вы ввели неправильные значения. Повторите операцию", "Ошибка!", JOptionPane.PLAIN_MESSAGE);
				}
			}
			System.out.println("x = " + x);
			while(((y<0) || (y>9)) || (a == 0 && y>6)){
				try{
					String w = JOptionPane.showInputDialog(null, "ВВедите координату y (от 1 до 10)");
					y = Integer.parseInt(w) - 1;
				if(((y<0) || (y>9)) || (a == 0 && y>6)){
					throw new Exception("Blet");
					}
				}catch(Exception e){
					y = 11;
					JOptionPane.showMessageDialog(null, "Вы ввели неправильные значения. Повторите операцию", "Ошибка!", JOptionPane.PLAIN_MESSAGE);
				}
			}
			System.out.println("y = " + y);
			plant4Ship(x,y, a,Field1,Zap1);
		
	}
	static void CreateNShip(int Field1[][], int Zap1[][], int Numer){
		boolean flag = false;
		boolean m = false;
		int a =0;
		int x = 11;
		int y = 11;
		while(m == false){
			a = 3;
			x = 11;
			y = 11;
			while(a<0 || a>1){
				try{
					String v = JOptionPane.showInputDialog(null, "Расположение. 1- горизонт. 0 - вертикальное");
					char g = v.charAt(0);
					a = ((int)g)-48;
				if(a<0 || a>1){
					throw new Exception("Blet");
				}
			}catch(Exception e){
					a = 11;
					JOptionPane.showMessageDialog(null, "Вы ввели неправильные значения. Повторите операцию", "Ошибка!", JOptionPane.PLAIN_MESSAGE);
			}
		}
			
			while(((x<0) || (x>9))|| (a == 1 && x>(10-Numer))){
				try{
					String h = JOptionPane.showInputDialog(null, "ВВедите координату x (от A до J)");
					char g = h.charAt(0);
					x = ((int)g)-65;
					if(((x<0) || (x>9))|| (a == 1 && x>(10-Numer))){
						throw new Exception("Blet");
					}
				}catch(Exception e){
					x = 11;
					JOptionPane.showMessageDialog(null, "Вы ввели неправильные значения. Повторите операцию", "Ошибка!", JOptionPane.PLAIN_MESSAGE);
				}
			}
			System.out.println("x = " + x);
			while(((y<0) || (y>9)) || (a == 0 && y>(10-Numer))){
				try{
					String w = JOptionPane.showInputDialog(null, "ВВедите координату y (от 1 до 10)");
					y = Integer.parseInt(w) - 1;
				if(((y<0) || (y>9))|| (a == 0 && y>(10-Numer))){
					throw new Exception("Blet");
					}
				}catch(Exception e){
					y = 11;
					JOptionPane.showMessageDialog(null, "Вы ввели неправильные значения. Повторите операцию", "Ошибка!", JOptionPane.PLAIN_MESSAGE);
				}
			}
			m = ChekTheDostup(Zap1, x, y,a, Numer, Field1, flag);
		}
		plantNShip(x,y, a,Field1,Zap1,Numer);
		
	}
	static void PrintFields(char Alphabet1[], int column1[], int urField1[][], int comonField1[][], int countShips[]){
		for(int i =0; i<11; i++){
				if(i == 1){
					System.out.print("  ");
				}
				System.out.print(Alphabet1[i]);
			}
			for(int i =0; i<10; i++){
				System.out.println("");
				if(i == 9){
					System.out.print(column1[i] +" ");
				}else{
				System.out.print(column1[i] + "  ");
				}
				for(int j = 0; j<10; j++){
					System.out.print(urField1[i][j]);
				}
			}
			System.out.println("");
			System.out.println("");
			System.out.print("Поле противника");
			System.out.println("");
			for(int i =0; i<11; i++){
				if(i == 1){
					System.out.print("  ");
				}
				System.out.print(Alphabet1[i]);
			}
			for(int i =0; i<10; i++){
				System.out.println("");
				if(i == 9){
					System.out.print(column1[i] +" ");
				}else{
				System.out.print(column1[i] + "  ");
				}
				for(int j = 0; j<10; j++){
					System.out.print(comonField1[i][j]);
					if(i == 8 && j == 9){
						System.out.print("          Ваше Количество кораблей= " + countShips[1]);
					}
					if(i == 9 && j == 9){
						System.out.print("          Количество кораблей противника= " + countShips[0]);
					}
				}
			}
	}
	static void PrintFields(char Alphabet1[], int column1[], int urField1[][]){
		for(int i =0; i<11; i++){
				if(i == 1){
					System.out.print("  ");
				}
				System.out.print(Alphabet1[i]);
			}
			for(int i =0; i<10; i++){
				System.out.println("");
				if(i == 9){
					System.out.print(column1[i] +" ");
				}else{
				System.out.print(column1[i] + "  ");
				}
				for(int j = 0; j<10; j++){
					System.out.print(urField1[i][j]);
				}
		}
			
	}
	static void plant4Ship(int cordinateX, int cordinateY, int a, int Field1[][], int Zap1[][]){
		int b = 3;
		if(a == 0){
			b = 3;
			for(int i = cordinateY; i<(cordinateY+4); i++){
				Field1[i][cordinateX] = 1;
				}
			}else{
			for(int i = cordinateX; i<(cordinateX+4); i++){
				Field1[cordinateY][i] = 1;
				}
			}
			UpdateZapretUr(Zap1,cordinateX,cordinateY,b,a);
	}
	static void plantNShip(int cordinateX, int cordinateY, int a, int Field1[][], int Zap1[][], int Numer){
		int b = Numer-1;
		if(a == 0){
			b = Numer-1;
			for(int i = cordinateY; i<(cordinateY+Numer); i++){
				Field1[i][cordinateX] = 1;
				}
			}else{
			for(int i = cordinateX; i<(cordinateX+Numer); i++){
				Field1[cordinateY][i] = 1;
				}
			}
			UpdateZapretUr(Zap1,cordinateX,cordinateY,b,a);
	}
	static void CreateAnalyseField(int AnalyseField[][], int NumerPaluba){
		boolean b = false;
		int a = 0;
			for(int i = 0; i<(10-(NumerPaluba-2)); i++){
				a--;
				if(i%NumerPaluba == 0){
					a = -1;
				}
				for(int k = 0; k<(10-(NumerPaluba-2)); k++){
					a++;
					if(a == 0){
						AnalyseField[i][k] = 0;
					a = -NumerPaluba;
					}else{
						AnalyseField[i][k] = 3;
					}

			}
		}
		if(NumerPaluba == 4){
			AddAdditionalFieldsFour(AnalyseField);
		}
		if(NumerPaluba == 3){
			AddAdditionalFieldThree(AnalyseField);
			//AddProstrele(AnalyseField);
		}
		if(NumerPaluba == 2){
			//AddProstrele(AnalyseField);
		}
	}
	static void AddAdditionalFieldsFour(int AnalyseField[][]){
		for(int i = 9; i>7; i--){
			int a = -1;
			a--;
			if(i%4 == 0){
				a = -1;
			}
			for(int k = 0; k<10; k++){
				a++;
				if(a == 0){
					AnalyseField[i][k] = 0;
					a = -4;
				}else{
					AnalyseField[i][k] = 3;
				}

			}
		}
		for(int i = 0; i<8; i++){
				for(int k = 8; k<10; k++){
						AnalyseField[i][k] = 3;

			}
		}
		AnalyseField[0][8] = 0;
		AnalyseField[1][9] = 0;
		AnalyseField[4][8] = 0;
		AnalyseField[5][9] = 0;
			
	}
	static void AddAdditionalFieldThree(int AnalyseField[][]){
		int g = 9;
		for(int i = 0; i<10; i++){
			if(i%3 == 0){
				AnalyseField[i][g] = 0;
			}
			else{
				AnalyseField[i][g] = 3;
			}
		}
		for(int i = 0; i<10; i++){
			if(i%3 == 0){
				AnalyseField[g][i] = 0;
			}
			else{
				AnalyseField[g][i] = 3;
			}
		}
	}
	static void AddProstrele(int AnalyseField[][], int poleMy[][]){
		for(int i = 0; i<10; i++){
			for(int j=0; j<10;j++){
				if(poleMy[i][j]>1){
					AnalyseField[i][j] = 3;
				}
			}
		}		
	}
	static void UpdateZapretUr(int Zap1[][], int cordinateX, int cordinateY, int b, int a){
			for(int i = cordinateY-1; i<cordinateY+b-(b*a)+2; i++){
				if(i>-1 && i<10){
					for(int j = cordinateX-1; j<cordinateX+(b*a)+2; j++){
						if(j>-1 && j<10){
							//System.out.println("Zap [" + i + "][" + j);
							Zap1[i][j] = 3;
						}
					}
				}
			}
		}
	static boolean ChekTheDostup(int Zap1[][],int x,int y,int a,int  Numer,int Field1[][], boolean z){
		int b = 0;
		if(a == 0){
			b = Numer-1;
			for(int i = y; i<(y+Numer); i++){
				if(Zap1[i][x] == 3){
					if(z == false){
							JOptionPane.showMessageDialog(null, "здесь расположить корабль невозможно", "здесь расположить корабль невозможно", JOptionPane.PLAIN_MESSAGE);		}
							return false;
				}
			}
		}else{
			for(int i = x; i<(x+Numer); i++){
				if(Zap1[y][i] == 3){
					if(z == false){
							JOptionPane.showMessageDialog(null, "здесь расположить корабль невозможно", "здесь расположить корабль невозможно", JOptionPane.PLAIN_MESSAGE);		}
							return false;
				}
			}
		}
		return true;
	}
	static void DeliteInComon(int Comon[][], int b, int x, int y, int a){
		//boolean checkPalubnick = checkOdnoPalubnick(x,y, Comon);
		//if(checkPalubnick){
		//	b = 0;
		//}
		for(int i = y-1; i<y+b-(b*a)+2; i++){
				if(i>-1 && i<10){
					for(int j = x-1; j<x+(b*a)+2; j++){
						if(j>-1 && j<10){
							//System.out.println("Zap [" + i + "][" + j + "]");
							Comon[i][j] = 2;
						}
					}
				}
			}
		if(a == 0){
			int j = x;
				for(int i = y; i<y+b+1; i++){
					if(i>-1 && i<10){
						Comon[i][j] = 6;
				}
			}
		}else{
			int i = y;
				for(int j = x; j<x+b+1; j++){
					if(j>-1 && j<10){
						Comon[i][j] = 6;
				}
			}
		}
	}
	static void DeliteInComon2(int AnalyseField[][], int Comon[][],int b, int x, int y, int a){
		boolean checkPalubnick = checkOdnoPalubnick(x,y, Comon);
		if(checkPalubnick){
			b = 0;
		}
		for(int i = y-1; i<y+b-(b*a)+2; i++){
				if(i>-1 && i<10){
					for(int j = x-1; j<x+(b*a)+2; j++){
						if(j>-1 && j<10){
							//System.out.println("Zap [" + i + "][" + j + "]");
							Comon[i][j] = 2;
							AnalyseField[i][j] = 3;
						}
					}
				}
			}
		if(a == 0){
			int j = x;
				for(int i = y; i<y+b+1; i++){
					if(i>-1 && i<10){
						Comon[i][j] = 6;
						AnalyseField[i][j] = 3;
				}
			}
		}else{
			int i = y;
				for(int j = x; j<x+b+1; j++){
					if(j>-1 && j<10){
						Comon[i][j] = 6;
						AnalyseField[i][j] = 3;
				}
			}
		}
	}
	static void MadeVystrel(char Alphabet[],int column[],int urField[][],int comonField[][] ,int PoleI[][], int comon[][],int countShips[]){
		boolean a = true;
		int x = 0;
		int y = 0;
		while(a == true && countShips[0] > 0){
		System.out.println("");
		PrintFields(Alphabet, column, urField, comonField, countShips);
		do{
		x = 11; // а может сразу задать число 11?
		y = 11;
		while(((x<0) || (x>9)) || ((y<0) || (y>9))){
			try{
				String z = JOptionPane.showInputDialog(null, "ВВедите координату выстрела x (от A до J)");
				String w = JOptionPane.showInputDialog(null, "ВВедите координату выстрела y (от 1 до 10)");
				char g = z.charAt(0);
				x = ((int)g)-65;
				y = Integer.parseInt(w) - 1;
				if(((x<0) || (x>9)) || ((y<0) || (y>9))){
					throw new Exception("Blet");
				}
			}catch(Exception e){
				x = 11;
				JOptionPane.showMessageDialog(null, "Куда стреляешь, щегол???", "ААААА!!!11!!???", JOptionPane.PLAIN_MESSAGE);
			}
		}
		System.out.println("x = " + x);
		System.out.println("y = " + y);
		if(comon[y][x]>1){
			JOptionPane.showMessageDialog(null, "Выстрел Невозможен!", "Выстрел Невозможен!", JOptionPane.PLAIN_MESSAGE);
		}
		}while(comon[y][x]>1);
		if(PoleI[y][x] == 0){
			JOptionPane.showMessageDialog(null, "Мимо!Ход Противника!", "Мимо!Ход Противника!", JOptionPane.PLAIN_MESSAGE);
			a = false;
			comon[y][x] = 3;
		}
		else{	
			int [] Wow = new int[]{0,0,0,0,0,0};
			WowSuch(Wow,PoleI, x, y);
				System.out.println("ТУУУУУТ2");
				if(Wow[0] == 0){
					System.out.println("KraiynY= " + Wow[3]);
					System.out.println("KraiynminY= " + Wow[2]);
					System.out.println("KraiynX= " + Wow[5]);
					System.out.println("KraiynminX= " + Wow[4]);
					System.out.println("count= " + Wow[0]);
					System.out.println("count2= " + Wow[1]);
					System.out.println("ТУУУУУТ4");
					comon[y][x] = 4;
					PoleI[y][x] = 4;
					countShips[0]--;					
					if((Wow[2] == 0 && Wow[3] == 0) && (Wow[5] == 0 && Wow[4] == 0)){
						DeliteInComon(comon, 0, x, y, 1);
							}
					if(Wow[2] == 0 && Wow[3] == 0){
						DeliteInComon(comon, Wow[1], (x+Wow[4]), y,1);
						}
					if(Wow[4]== 0 && Wow[5] == 0){
						DeliteInComon(comon, Wow[1], x, (y+Wow[2]), 0);
				}
				JOptionPane.showMessageDialog(null, "Корабль Противника уничтожен", "Уничтожен", JOptionPane.PLAIN_MESSAGE);
			}else{
				System.out.println("KraiynY= " + Wow[3]);
				System.out.println("KraiynminY= " + Wow[2]);
				System.out.println("KraiynX= " + Wow[5]);
				System.out.println("KraiynminX= " + Wow[4]);
				System.out.println("count= " + Wow[0]);
				System.out.println("count2= " + Wow[1]);
				System.out.println("ТУУУУУТ4");
				JOptionPane.showMessageDialog(null, "Есть пробитие!", "Есть пробитие!", JOptionPane.PLAIN_MESSAGE);	
				comon[y][x] = 4;
				PoleI[y][x] = 4;
		 }
		}	

	}
	}
	static void EnemyVystrel(int PoleMy[][], int MemoryRand[],int AnalyseField[][],int countShips[]){
		boolean a = false;
		String Zapomny = "";
		while(a == false && countShips[1] > 0){
			if(MemoryRand[6] == 0){
				randomFire(PoleMy,MemoryRand,countShips,AnalyseField);
				System.out.println("x = " + MemoryRand[7]);
				System.out.println("y = " + MemoryRand[8]);
					if(PoleMy[MemoryRand[8]][MemoryRand[7]] == 3){
						a = true;
					}
					if(PoleMy[MemoryRand[8]][MemoryRand[7]] == 4){
						MemoryRand[6] = 1;
						//Popadanie();
					}
					if(PoleMy[MemoryRand[8]][MemoryRand[7]] == 6){
						//Unichtozhen();
					}
			}else{
				int [] Cordinates = aimFire(PoleMy,MemoryRand,countShips,AnalyseField);
				System.out.println("V Enemy Vystrel x= " + Cordinates[0] + "y= " + Cordinates[1] + "Значение в поле равно= " + PoleMy[Cordinates[1]][Cordinates[0]]);
				if(PoleMy[Cordinates[1]][Cordinates[0]] == 3 || MemoryRand[9] > 9){
					a = true;
					MemoryRand[4] = 0;
					if(MemoryRand[9] > 9){
						JOptionPane.showMessageDialog(null, "ОйОщибкаПоймана", "ПойПойПойНа!", JOptionPane.PLAIN_MESSAGE);
					}
				}
				if(PoleMy[Cordinates[1]][Cordinates[0]] == 4 && MemoryRand[9] <10){
					MemoryRand[6] = 1;
				}
				if(PoleMy[Cordinates[1]][Cordinates[0]] == 6){
					MemoryRand[6] = 0;
					a = false;
				}
			}
		}		
	}
	static void randomFire(int PoleMy[][],int MemoryRand[],int countShips[], int AnalyseField[][]){
		boolean a = true;
		while(a == true){
			//String z = JOptionPane.showInputDialog(null, "ВВедите координату выстрела x (от A до J)");
			//String w = JOptionPane.showInputDialog(null, "ВВедите координату выстрела y (от 1 до 10)");
			//char g = z.charAt(0);
			//MemoryRand[7] = ((int)g)-65;
			//MemoryRand[8] = Integer.parseInt(w) - 1;	
			MemoryRand[7] = (int)(((Math.random())*10)-0.00000001);
			MemoryRand[8] = (int)(((Math.random())*10)-0.00000001);
			if(MemoryRand[10] == 1){
			a = CheckTheFire(PoleMy, MemoryRand[8],MemoryRand[7]);
			}
			else{
			a = CheckTheFire2(AnalyseField,PoleMy, MemoryRand[8],MemoryRand[7], MemoryRand[10]);
			}
		}
		System.out.println("координаты рандомного выстрела x= " + MemoryRand[7] + " y= " + MemoryRand[8]);
		if(PoleMy[MemoryRand[8]][MemoryRand[7]] == 0){
			JOptionPane.showMessageDialog(null, "Противник промахнулся!", "Противник Промахнулся!", JOptionPane.PLAIN_MESSAGE);
			PoleMy[MemoryRand[8]][MemoryRand[7]] = 3;
			AnalyseField[MemoryRand[8]][MemoryRand[7]] = 3;
		}else{
			int [] Wow = new int[]{0,0,0,0,0,0};
			WowSuch(Wow,PoleMy, MemoryRand[7], MemoryRand[8]);
			PoleMy[MemoryRand[8]][MemoryRand[7]] = CheckSheepStat(Wow,MemoryRand[8],MemoryRand[7],PoleMy,countShips,AnalyseField,MemoryRand);
		}
	}
	static boolean CheckTheFire(int Pole[][],int y, int x){
		if(Pole[y][x] >1){
			return true;
		}else{
			return false;
		}
	}
	static boolean CheckTheFire2(int AnalyseField[][], int PoleMy[][] ,int y, int x, int a){
		if(AnalyseField[y][x] >1){
			return true;
		}else{
			boolean u = CheckFreeSpace(PoleMy,y,x,a);
			return u;
		}
	}
	static boolean CheckFreeSpace(int PoleMy[][], int y, int x, int a){
		int c = 1;
		int d = 1;
		while((c<a)&&((c+y)<10)&&(PoleMy[y+c][x]<2)){
			c++;
		}
		while((d<a)&&((y-d)>-1)&&(PoleMy[y-d][x]<2)){
			d++;
		}
		System.out.println("c+d по игреку = " + (c+d));
		if((c+d) > a){
			return false;
		}
		c = 0;
		d = 0;
		while((c<a)&&((c+x)<10)&&(PoleMy[y][x+c]<2)){
			c++;
		}
		while((d<a)&&((x-d)>-1)&&(PoleMy[y][x-d]<2)){
			d++;
		}
		System.out.println("c+d по иксу = " + (c+d));
		if((c+d) > a){
			return false;
		}
		return true;
	}
			
	static void WowSuch(int Fun[],int PoleI[][], int x,int  y){
			//System.out.println("ТУУУУУТ1");
				for(int i = y-1; ((i>-1)&&((i>(y-4))&& ((PoleI[i][x] != 0) && (PoleI[i][x] != 3)))); i--){
					if((PoleI[i][x] ==4 || PoleI[i][x] == 1)){
						if(PoleI[i][x] == 4){
							Fun[1]++; 
						}if(PoleI[i][x] == 1){
							Fun[0]++;
						}
					Fun[2]--;
					}
				}

				for(int i = y+1; ((i<10)&&((i<(y+4))&& ((PoleI[i][x] != 0) && (PoleI[i][x] != 3)))); i++){
					if((PoleI[i][x] ==4 || PoleI[i][x] == 1)){
						if(PoleI[i][x] == 4){
							Fun[1]++;
						}if(PoleI[i][x] == 1){
							Fun[0]++;
						}
					Fun[3]++;
					}
				}

				for(int i = x-1;  ((i>-1)&&((i>(x-4))&& ((PoleI[y][i] != 0) && (PoleI[y][i] != 3)))); i--){
					if((PoleI[y][i] ==4 || PoleI[y][i] == 1)){
						if(PoleI[y][i] == 4){
							Fun[1]++;
						}if(PoleI[y][i] == 1){
							Fun[0]++;
						}
					Fun[4]--;
					}
				}

				for(int i = x+1; ((i<10)&&((i<(x+4))&& ((PoleI[y][i] != 0) && (PoleI[y][i] != 3)))); i++){
					if((PoleI[y][i] ==4 || PoleI[y][i] == 1)){
						if(PoleI[y][i] == 4){
							Fun[1]++;
						}if(PoleI[y][i] == 1){
							Fun[0]++;
						}
					Fun[5]++;
					}
				}
	}
			
	static int CheckSheepStat(int Fun[], int y, int x, int PoleI[][],int countShips[], int AnalyseField[][],int MemoryRand[]){
				if(Fun[0] == 0){
					System.out.println("KraiynY= " + Fun[3]);	
					System.out.println("KraiynminY= " + Fun[2]);
					System.out.println("KraiynX= " + Fun[5]);
					System.out.println("KraiynminX= " + Fun[4]);
					System.out.println("count= " + Fun[0]);
					System.out.println("count2= " + Fun[1]);
					//System.out.println("FAAAAAAAAAAAAAAAAAAN " + MemoryRand[10]);
					System.out.println("ТУУУУУТ4");
					if((Fun[2] == 0 && Fun[3] == 0) && (Fun[5] == 0 && Fun[4] == 0)){
						DeliteInComon2(AnalyseField,PoleI, 1, x, y, 1);
							}
					if(Fun[2] == 0 && Fun[3] == 0){
						DeliteInComon2(AnalyseField,PoleI,Fun[1], (x+Fun[4]), y,1);
						}
					if(Fun[4] == 0 && Fun[5] == 0){
						DeliteInComon2(AnalyseField,PoleI,Fun[1], x, (y+Fun[2]), 0);
				}
				//PoleI[y][x] = 6;
				countShips[1]--;
				if((Fun[1] == (MemoryRand[10]-1))&&((MemoryRand[10]-1)>0)){
					if(((MemoryRand[10]-1)*MemoryRand[MemoryRand[14]]) == Fun[1]){
							MemoryRand[MemoryRand[14]]--;
							int a = MemoryRand[MemoryRand[14]];
						while((a == 0)&&(MemoryRand[14]<14)){
							MemoryRand[10] = MemoryRand[10]-1;
							MemoryRand[14]++;
							a = MemoryRand[MemoryRand[14]];
						}
						if(MemoryRand[10]>1){
						CreateAnalyseField(AnalyseField, MemoryRand[10]);
						AddProstrele(AnalyseField,PoleI);
						}
						//Fun[1] = 0;
					}else{
						MemoryRand[MemoryRand[14]]--;
					}
				}else{
					switch(Fun[1]){
					case(2):
						MemoryRand[12]--;
						break;
					case(1):
						MemoryRand[13]--;
						break;
						}
				}
				//Fun[1] = 0;
				Unichtozhen();
				return 6;

			}else{
				System.out.println("KraiynY= " + Fun[3]);
				System.out.println("KraiynminY= " + Fun[2]);
				System.out.println("KraiynX= " + Fun[5]);
				System.out.println("KraiynminX= " + Fun[4]);
				System.out.println("count= " + Fun[0]);
				System.out.println("count2= " + Fun[1]);
				//PoleI[y][x] = 4;
				AnalyseField[y][x] = 3;
				Popadanie();
				return 4;

		 }
		}
	static int[] aimFire(int Pole[][],int MemoryRand[], int countShips[], int AnalyseField[][]){
		int ProstranstvoX = 0;
		int ProstranstvoY = 0;
		int u = 0;
		for(int i= 0; i<4;i++){
			u = u + MemoryRand[i];
		}
		if(u == 4){
			MemoryRand[9]++;
		}
		System.out.println("Direction = " + MemoryRand[4]);
		do{
		ProstranstvoX = 0;
		ProstranstvoY = 0;
		if(MemoryRand[4] == 0 && u<4){
		do{
		MemoryRand[5] = (int)(4*(Math.random()-0.0001));
		}while(MemoryRand[MemoryRand[5]] != 0);
		}
		if(((((MemoryRand[7]+MemoryRand[4]) == 0) && MemoryRand[5] == 1)  || (((MemoryRand[7]+MemoryRand[4]) == 9) && MemoryRand[5] == 0)  ||(((MemoryRand[8]+MemoryRand[4]) == 0) && MemoryRand[5] == 3) || (((MemoryRand[8]+MemoryRand[4]) == 9) && MemoryRand[5] == 2)) && MemoryRand[4]!= 0){
			MemoryRand[4] = 0;
			switch(MemoryRand[5]){
				case (0):
					MemoryRand[5] = 1;
					break;
				case (1):
					MemoryRand[5] = 0;
					break;
				case (2):
					MemoryRand[5] = 3;
					break;
				case (3):
					MemoryRand[5] = 2;
					break;
				}
		}
		MemoryRand[MemoryRand[5]] = 1;
		if(MemoryRand[5] == 0){
			ProstranstvoX = 1;
			}
		if(MemoryRand[5] == 1){
			ProstranstvoX = -1;
			}
		if(MemoryRand[5] == 2){
			ProstranstvoY =1;
			}
		if(MemoryRand[5] == 3){
			ProstranstvoY = -1;
			}
		}while((((MemoryRand[5] == 1)&&((MemoryRand[7]+ProstranstvoX) == -1)) || ((MemoryRand[5] == 0)&&((MemoryRand[7]+ProstranstvoX) == 10)) || ((MemoryRand[5] == 3)&&((MemoryRand[8]+ProstranstvoY) == -1)) || ((MemoryRand[5] == 2)&&((MemoryRand[8]+ProstranstvoY) == 10))));
		System.out.println("RANDOM = " + MemoryRand[5]);
		System.out.println("ProstranstvoX = " + ProstranstvoX);
		System.out.println("ProstranstvoY = " + ProstranstvoY);
		System.out.println("Cтарые координаты " + "x= " + MemoryRand[7] + " y= " + MemoryRand[8]);
		boolean ForBest = false;
		System.out.println("");
			for(int i = 0; i<4; i++){
				System.out.println("MemoryRand[" + i + "]= " + MemoryRand[i]);
			}
			System.out.println("");
			return chosingDirectionX(ProstranstvoX,ProstranstvoY,Pole,MemoryRand[7],MemoryRand[8], MemoryRand, countShips, AnalyseField);

		}
	static String WhatIsTheString(int x, int y){
		x= x+65;
		char e = (char)x;
		Character f = e;
		Integer d = y;
		return (f.toString() + d.toString());
		}
	static int[] chosingDirectionX(int ProstranstvoX,int ProstranstvoY, int Pole[][], int x, int y, int MemoryRand[], int countShips[], int AnalyseField[][]){
		//System.out.println("Здесь Пространство X равно = " + ProstranstvoX);
		//if((((x+ProstranstvoX+MemoryRand[4])<10)&&(x+ProstranstvoX+MemoryRand[4])>-1)){
				int y1 = y + ProstranstvoY + MemoryRand[4]*Math.abs(ProstranstvoY);
				int x1 = x + ProstranstvoX + MemoryRand[4]*Math.abs(ProstranstvoX);
				if(Pole[y1][x1]==1){
					int [] Wow = new int[]{0,0,0,0,0,0};
					WowSuch(Wow,Pole, x1, y1);
					Pole[y1][x1]=CheckSheepStat(Wow,y1,x1,Pole, countShips,AnalyseField,MemoryRand);
					if(Pole[y1][x1] == 4){
						/*if(ForBest = true){
						if(ProstranstvoX == 1){
							MemoryRand[0] = 1;
							MemoryRand[5] = 0;
						}else{
							MemoryRand[1] = 1;
							MemoryRand[5] = 1;
							}
						}*/
						MemoryRand[4] = MemoryRand[4] + ProstranstvoX+ProstranstvoY;
						if(ProstranstvoY == 0){
						FirstPopOrNotX(MemoryRand);
						}else{
						FirstPopOrNotY(MemoryRand);
						}
						System.out.println("Новые координаты " + "x= " + x1 + " y= " + y1 + " Сработало тут Намба Уан");	
						int [] Cordinates = new int[]{x1,y1};
						return Cordinates;
					}else{
						MemoryRand = ManInBlack(MemoryRand);
						int [] Cordinates = new int[]{x,y};
						return Cordinates;
					}
				}else{
					/*if(ForBest = true){
						if(ProstranstvoX == 1){
							MemoryRand[0] = 1;
						}else{
							MemoryRand[1] = 1;
							}
						}
					}*/
					if(Pole[y1][x1] == 0){
						System.out.println("Новые координаты " + "x= " + x + " y= " + y+ " Сработало тут Намба Сри");			
						Pole[y1][x1] = 3;
						AnalyseField[y1][x1] = 3;
						Promah();
						int [] Cordinates = new int[]{x1, y1};
						return Cordinates;
					}
					if(Pole[y1][x1] == 2 || Pole[y1][x1] == 3){
						MemoryRand[4] = 0;
						int [] Cordinates = new int[]{x,y};
						return Cordinates;	
					}
				}
		/*ProstranstvoX = 1 - (2*(((int)(Math.random() + 0.5))/1));
		ForBest = true;
		MemoryRand[4] = 0;
		System.out.println("Попадание сюда!!!! " + "pROSTRANSTVOXtoY= " + ProstranstvoX);
		pont--;
		if(pont>0){
		return chosingDirectionY(ProstranstvoX,Pole,x,y, ForBest, MemoryRand, countShips, pont,AnalyseField );
		}
		else{
			System.out.println("ПРЕРЫВАНИЕ АХТУНГ!");
			int [] Cordinates = new int[]{x,y};
			return Cordinates;
		}	*/
		int [] Cordinates = new int[]{x,y};
		return Cordinates;
	}

	static void Promah(){
		JOptionPane.showMessageDialog(null, "Противник промахнулся!", "Противник Промахнулся!", JOptionPane.PLAIN_MESSAGE);
	}
	static void Popadanie(){
		JOptionPane.showMessageDialog(null, "Противник попал", "Попадание!", JOptionPane.PLAIN_MESSAGE);
	}	
	static void Unichtozhen(){
		JOptionPane.showMessageDialog(null, "Противник уничтожил корабль", "Уничтожен", JOptionPane.PLAIN_MESSAGE);
	}
	static int[] ManInBlack (int[] Change){
		for(int i = 0; i<10; i++){
			Change[i] = 0;
		}
		return Change;
	}
	static void FirstPopOrNotX(int MemoryRand[]){
			MemoryRand[2] = 1;
			MemoryRand[3] = 1;
	}
	static void FirstPopOrNotY(int MemoryRand[]){		
			MemoryRand[0] = 1;
			MemoryRand[1] = 1;
	}
	static boolean checkOdnoPalubnick(int x, int y, int Comon[][]){
		int a = 1;
		//System.out.println("КООООООООООООРДИНАТЫ РАВНЫ = XXXXXX=" + x + " YYYYYYY=" +y);
		//System.out.println("Первый пошел" + Comon[y][x+a]);
		//System.out.println("Второй пошел" + Comon[y+a][x]);
		if(x+a<10){
			if(Comon[y][x+a] == 4||Comon[y][x+a] == 6||Comon[y][x+a] == 1 ){
				return false;
			}
		}
		if(y+a<10){
			if(Comon[y+a][x] == 4||Comon[y+a][x] == 6||Comon[y+a][x] == 1){
				return false;
			}
		}
		a = -1;
		//System.out.println("Третий пошел" + Comon[y][x+a]);
		//System.out.println("ЧЕТВЕРТЫЙ пошел" + Comon[y+a][x]);
		if(x+a>-1){
			if(Comon[y][x+a] == 4||Comon[y][x+a] == 6||Comon[y][x+a] == 1){
				return false;
			}
		}
		if(y+a<-1){
			if(Comon[y+a][x] == 4||Comon[y+a][x] == 6||Comon[y+a][x] == 1){
				return false;
			}
		}
	return true;
	}
}	