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
	
	public boolean insertMovie(Movie1 m)throws Exception{
		// DB logic
		
		Connection c = DriverManager.getConnection("jdbc:mysql://localhost:3306/demodb","root","Jahnavee45&");
		Statement s = c.createStatement();
		boolean b = s.execute("insert into movie values("+m.getMovieid()+",'"+m.getMoviename()+"','"+m.getCast1()+"','"+m.getCast2()+"','"+m.getReleasedate()+"','"+m.getLanguage()+"',"+m.getLength()+",'"+m.getMovietype()+"',"+m.getProductionid()+")");
		c.close();
		return false;
	}
	
	public List<Movie1> getAllMovies()throws Exception{
		List<Movie1> al = new ArrayList<Movie1>();
		
		Connection c = DriverManager.getConnection("jdbc:mysql://localhost:3306/demodb","root","Jahnavee45&");
		PreparedStatement ps = c.prepareStatement("select * from movie");
		ResultSet rs = ps.executeQuery();
		
		while(rs.next()) {
			al.add(new Movie1(rs.getInt(1),rs.getString(2),rs.getString(3),rs.getString(4),rs.getString(5),rs.getString(6),rs.getInt(7), rs.getString(8), rs.getInt(9)));
		}
		c.close();
		return al;
		
		
	}
	
	public boolean updateMovie(Movie1 m)throws Exception{
		
		String sql = "update movie set movieid=? where moviename=?";
		Scanner sc = new Scanner(System.in);
		System.out.println("Enter the moviename to update movieid");
		String moviename = sc.next();
		System.out.println("Enter updated movieid");
		int movieid = sc.nextInt();
		try(Connection c = DriverManager.getConnection("jdbc:mysql://localhost:3306/demodb","root","Jahnavee45&");
		PreparedStatement ps = c.prepareStatement(sql);){
			ps.setInt(1,movieid);
			ps.setString(2,moviename);
			ps.executeUpdate();
		} catch(SQLException e) {
			e.printStackTrace();
		}
		
		return false;
		
	}
	
	public boolean deleteMovie(Movie1 m)throws Exception{
		String sql = "delete from movie where movieid=?";
		Scanner sc = new Scanner(System.in);
		System.out.println("Enter movieid");
		int movieid = sc.nextInt();
		try(Connection c = DriverManager.getConnection("jdbc:mysql://localhost:3306/demodb","root","Jahnavee45&");
		PreparedStatement ps = c.prepareStatement(sql);){
			ps.setInt(1,movieid);
			ps.executeUpdate();
		} catch(SQLException e) {
			e.printStackTrace();
		}
		return false;
		
	}

}
