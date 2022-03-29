package com.ltts.movieproject.main;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.Statement;
import java.util.*;

import com.ltts.movieproject.bo.MovieBo;
import com.ltts.movieproject.model.Movie1;
public class MovieMain {

	public static void main(String[] args)throws Exception {
		// TODO Auto-generated method stub
		
		Scanner sc =new Scanner(System.in);
		System.out.println("1.Insert movie details");
		System.out.println("2.View Movie");
		System.out.println("3.Update movieId");
		System.out.println("4.Delete a movie row");
		
		MovieBo mb = new MovieBo();
		int n = sc.nextInt();
		
		switch(n) {
		case 1:
			System.out.println("Enter movieId");
			int movieid = sc.nextInt();
			System.out.println("Enter moviename");
			String moviename = sc.next();
			System.out.println("Enter actor name");
		    String cast1 = sc.next();
			System.out.println("Enter actress name");
			String cast2 = sc.next();
			System.out.println("Enter releasedate");
			String releasedate = sc.next();
			System.out.println("Enter language");
			String language = sc.next();
			System.out.println("Enter length");
			int length = sc.nextInt();
			System.out.println("Enter movietype");
			String movietype = sc.next();
			System.out.println("Enter productionId");
			int productionid = sc.nextInt();
			
			//DB logic
			Movie1 m = new Movie1(movieid,moviename,cast1,cast2,releasedate,language,length,movietype,productionid);
			boolean b = mb.insertMovie(m);
			if(b==false) {
				System.out.println("Values inserted...");
			}
			break;
		case 2:
			System.out.println("Movie details");
			List<Movie1> li = mb.getAllMovies();
			for(Movie1 m1:li) {
				System.out.println(m1);
			}
			break;
		case 3:
			Movie1 m1 = new Movie1();
			System.out.println("Update movieid");
			boolean b1 = mb.updateMovie(m1);
			if(b1==false) {
				System.out.println("Updated movieid");
			}
			break;
		case 4:
			Movie1 m2 = new Movie1();
			System.out.println("Delete movie detail");
			boolean b2 = mb.deleteMovie(m2);
			if(b2==false) {
				System.out.println("Deleted successfully!!!");
			}
			break;
		  }
		}

}
