import java.util.Scanner;
public class Main {
	static int count =0;
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		int m = sc.nextInt();
		char[][] arr = new char[n][m];
		for (int i = 0; i < arr.length; i++) {
			String s = sc.next();
			for (int j = 0; j < arr[i].length; j++) {
				arr[i][j] = s.charAt(j);
			}
		}
		int ans[][] = new int[n][m];
		rat(arr,0,0,n-1,m-1,ans);
		if(count==0) {
			System.out.println("NO PATH FOUND");
		}
	}
	public static void rat(char[][] arr, int cr, int cc, int n, int m, int[][] ans) {
		if(cr == n && cc == m) { 
			count++;
			ans[cr][cc] = 1;
			Display(ans);
			return;
		}
		if(cr<0 || cc<0 || cr>n || cc>m || arr[cr][cc] =='X') {
			return; 
		}
		ans[cr][cc] =1;
		arr[cr][cc] = 'X';
		rat(arr, cr+1, cc, n, m, ans);
		rat(arr, cr, cc+1, n, m, ans);
		rat(arr, cr-1, cc, n, m, ans);
		rat(arr, cr, cc-1, n, m, ans);
		ans[cr][cc] = 0;
		arr[cr][cc] = 'O';	
	}
	private static void Display(int[][] ans) {
		for (int a []: ans) {
			for (int i : a) {
				System.out.print(i+ " ");
			}
			System.out.println();
		}
		
	}

}
