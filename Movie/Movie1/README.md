package com.ltts.movieproject.model;

public class Movie1 {

	private int movieid;
	private String moviename;
	private String cast1;
	private String cast2;
	private String releasedate;
	private String language;
	private int length;
	private String movietype;
	private int productionid;
	
	public Movie1(){
		super();
	}
	public Movie1(int movieid, String moviename, String cast1, String cast2, String releasedate, String language, int length,
			String movietype, int productionid) {
		// TODO Auto-generated constructor stub
		this.movieid = movieid;
		this.moviename=moviename;
		this.cast1=cast1;
		this.cast2=cast2;
		this.releasedate=releasedate;
		this.language=language;
		this.length=length;
		this.movietype=movietype;
		this.productionid=productionid;
	}
	public int getMovieid() {
		return movieid;
	}
	public void setMovieid(int movieid) {
		this.movieid = movieid;
	}
	public String getMoviename() {
		return moviename;
	}
	public void setMoviename(String moviename) {
		this.moviename = moviename;
	}
	public String getCast1() {
		return cast1;
	}
	public void setCast1(String cast1) {
		this.cast1 = cast1;
	}
	public String getCast2() {
		return cast2;
	}
	public void setCast2(String cast2) {
		this.cast2 = cast2;
	}
	public String getReleasedate() {
		return releasedate;
	}
	public void setReleasedate(String releasedate) {
		this.releasedate = releasedate;
	}
	public String getLanguage() {
		return language;
	}
	public void setLanguage(String language) {
		this.language = language;
	}
	public int getLength() {
		return length;
	}
	public void setLength(int length) {
		this.length = length;
	}
	public String getMovietype() {
		return movietype;
	}
	public void setMovietype(String movietype) {
		this.movietype = movietype;
	}
	public int getProductionid() {
		return productionid;
	}
	public void setProductionid(int productionid) {
		this.productionid = productionid;
	}
	@Override
	public String toString() {
		// TODO Auto-generated method stub
		return "Movie1[movieid="+movieid+",moviename="+moviename+",cast1="+cast1+",cast2="+cast2+",releasedate="+releasedate+",language="+language+",length="+length+",movietype="+movietype+",productioid="+productionid+"]";
	}
	
	

}
