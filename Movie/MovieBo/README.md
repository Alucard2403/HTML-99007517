package com.ltts.movieproject.bo;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;
import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

import com.ltts.movieproject.model.Movie1;

//import com.ltts.movieproject.main.MovieMain;

public class MovieBo {
	Scanner sc =new Scanner(System.in);
	public boolean insertMovie(Movie1 m)throws Exception{
		// DB logic
		
		Connection c = DriverManager.getConnection("jdbc:mysql://localhost:3306/jai","root","Jai@2403");
		Statement s = c.createStatement();
		boolean b = s.execute("insert into movie values("+m.getMovieid()+",'"+m.getMoviename()+"','"+m.getCast1()+"','"+m.getCast2()+"','"+m.getReleasedate()+"','"+m.getLanguage()+"',"+m.getLength()+",'"+m.getMovietype()+"',"+m.getProductionid()+")");
		c.close();
		return false;
	}
	
	public List<Movie1> getAllMovies()throws Exception{
		List<Movie1> al = new ArrayList<Movie1>();
		
		Connection c = DriverManager.getConnection("jdbc:mysql://localhost:3306/jai","root","Jai@2403");
		PreparedStatement ps = c.prepareStatement("select * from movie");
		ResultSet rs = ps.executeQuery();
		
		while(rs.next()) {
			al.add(new Movie1(rs.getInt(1),rs.getString(2),rs.getString(3),rs.getString(4),rs.getString(5),rs.getString(6),rs.getInt(7), rs.getString(8), rs.getInt(9)));
		}
		c.close();
		return al;
		
		
	}
	
	public boolean updateMovie(Movie1 m)throws Exception{
		
		System.out.println("1.Update Moviename");
		System.out.println("2.Update Heroname");
		System.out.println("3.Update Heroine");
		System.out.println("4.Update Language");
		System.out.println("5.Update Length");
		
		
		int n = sc.nextInt();
		
		switch(n) {
		case 1:
			String sql = "update movie set moviename=? where movieid=?";
			Scanner sc = new Scanner(System.in);
			System.out.println("Enter the movieid to update moviename");
			int movieid = sc.nextInt();
			System.out.println("Enter updated moviename");
			String moviename = sc.next();
			try(Connection c = DriverManager.getConnection("jdbc:mysql://localhost:3306/jai","root","Jai@2403");
			PreparedStatement ps = c.prepareStatement(sql);){
				ps.setString(1,moviename);
				ps.setInt(2,movieid);
				ps.executeUpdate();
			} catch(SQLException e) {
				e.printStackTrace();
			}
	          break;	
		case 2:
			String s = "update movie set heroname=? where movieid=?";
			Scanner p = new Scanner(System.in);
			System.out.println("Enter the movieid to update heroname");
			int movieid2 = p.nextInt();
			System.out.println("Enter updated heroname");
			String heroname = p.next();
			try(Connection c = DriverManager.getConnection("jdbc:mysql://localhost:3306/jai","root","Jai@2403");
			PreparedStatement ps = c.prepareStatement(s);){
				ps.setString(1,heroname);
				ps.setInt(2,movieid2);
				ps.executeUpdate();
			} catch(SQLException e) {
				e.printStackTrace();
			}
			
			
			break;
		case 3:
			String o = "update movie set heroname=? where movieid=?";
			Scanner u = new Scanner(System.in);
			System.out.println("Enter the movieid to update heroname");
			int movieid3 = u.nextInt();
			System.out.println("Enter updated heroname");
			String heroine = u.next();
			try(Connection c = DriverManager.getConnection("jdbc:mysql://localhost:3306/jai","root","Jai@2403");
			PreparedStatement ps = c.prepareStatement(o);){
				ps.setString(1,heroine);
				ps.setInt(2,movieid3);
				ps.executeUpdate();
			} catch(SQLException e) {
				e.printStackTrace();
			}
			
			
			break;
		case 4:
			String Y = "update movie set Language=? where movieid=?";
			Scanner J = new Scanner(System.in);
			System.out.println("Enter the movieid to update language");
			int movieid4 = J.nextInt();
			System.out.println("Enter updated language");
			String language = J.next();
			try(Connection c = DriverManager.getConnection("jdbc:mysql://localhost:3306/jai","root","Jai@2403");
			PreparedStatement ps = c.prepareStatement(Y);){
				ps.setString(1,language);
				ps.setInt(2,movieid4);
				ps.executeUpdate();
			} catch(SQLException e) {
				e.printStackTrace();
			}
			
			break;
        case 5:
        	String sq = "update movie set length=? where movieid=?";
    		Scanner sp = new Scanner(System.in);
    		System.out.println("Enter the movieid to update length");
    		int movieid5 = sp.nextInt();
    		System.out.println("Enter updated length");
    		int length = sp.nextInt();
    		try(Connection c = DriverManager.getConnection("jdbc:mysql://localhost:3306/jai","root","Jai@2403");
    		PreparedStatement ps = c.prepareStatement(sq);){
    			ps.setInt(1,length);
    			ps.setInt(2,movieid5);
    			ps.executeUpdate();
    		} catch(SQLException e) {
    			e.printStackTrace();
    		}
    		
    	
			
			break;
		  }
		return false;
		
	}
	
	public boolean deleteMovie(Movie1 m)throws Exception{
		String sql = "delete from movie where movieid=?";
		Scanner sc = new Scanner(System.in);
		System.out.println("Enter movieid");
		int movieid = sc.nextInt();
		try(Connection c = DriverManager.getConnection("jdbc:mysql://localhost:3306/jai","root","Jai@2403");
		PreparedStatement ps = c.prepareStatement(sql);){
			ps.setInt(1,movieid);
			ps.executeUpdate();
		} catch(SQLException e) {
			e.printStackTrace();
		}
		return false;
		
	}

}
