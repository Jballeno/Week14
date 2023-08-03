"# Week14" 
package pet.park;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;


@SpringBootApplication
public class PetParkApplication {
	public static void main(String[] args) {
	SpringApplication.run(PetParkApplication.class, args);

	}

}

package pet.park.entity;

import java.util.HashSet;
import java.util.Set;

import jakarta.persistence.Entity;
import jakarta.persistence.GeneratedValue;
import jakarta.persistence.GenerationType;
import jakarta.persistence.Id;
import jakarta.persistence.ManyToMany;
import lombok.Data;

@Entity
@Data
public class Amenity {
	@Id
	@GeneratedValue(strategy = GenerationType.IDENTITY)
	private Long AmenityId;
	
	private String amenity;
	
	@ManyToMany(mappedBy = "amenities")
	private Set<PetPark> petParks = new HashSet<>();
	
	
}

package pet.park.entity;

import java.util.HashSet;
import java.util.Set;

import jakarta.persistence.CascadeType;
import jakarta.persistence.Column;
import jakarta.persistence.Entity;
import jakarta.persistence.GeneratedValue;
import jakarta.persistence.GenerationType;
import jakarta.persistence.Id;
import jakarta.persistence.OneToMany;
import lombok.Data;
import lombok.EqualsAndHashCode;
import lombok.ToString;

@Entity
@Data
public class Contributor {
	@Id
	@GeneratedValue(strategy = GenerationType.IDENTITY)
	private Long contributorId;
	
	
	private String contributorName;
	
	@Column(unique = true)
	private String contributorEmail;
	
	
	@EqualsAndHashCode.Exclude
	@ToString.Exclude
	@OneToMany(mappedBy = "contributor", cascade = CascadeType.ALL)
	private Set<PetPark> petParks = new HashSet<>();
}

package pet.park.entity;

import java.util.HashSet;
import java.util.Set;

import jakarta.persistence.CascadeType;
import jakarta.persistence.Column;
import jakarta.persistence.Entity;
import jakarta.persistence.GeneratedValue;
import jakarta.persistence.GenerationType;
import jakarta.persistence.Id;
import jakarta.persistence.OneToMany;
import lombok.Data;
import lombok.EqualsAndHashCode;
import lombok.ToString;

@Entity
@Data
public class Contributor {
	@Id
	@GeneratedValue(strategy = GenerationType.IDENTITY)
	private Long contributorId;
	
	
	private String contributorName;
	
	@Column(unique = true)
	private String contributorEmail;
	
	
	@EqualsAndHashCode.Exclude
	@ToString.Exclude
	@OneToMany(mappedBy = "contributor", cascade = CascadeType.ALL)
	private Set<PetPark> petParks = new HashSet<>();
}

spring:
  datasource:
    username: pet_parks
    password: pet_parks
    url: jdbc:mysql://localhost:3306/pet_parks
    
  jpa:
    hibernate:
      ddl-auto: create
    show-sql: true
    defer-datasource-initialization: true
    
  sql:
    init:
      mode: always 
	 
INSERT INTO amenity (amenity) VALUES ('dog friendly');
INSERT INTO amenity (amenity) VALUES ('cat friendly');
INSERT INTO amenity (amenity) VALUES ('turtle friendly');
INSERT INTO amenity (amenity) VALUES ('chicken friendly');
INSERT INTO amenity (amenity) VALUES ('restrooms');
INSERT INTO amenity (amenity) VALUES ('fenced area');
INSERT INTO amenity (amenity) VALUES ('hot dog stand');
INSERT INTO amenity (amenity) VALUES ('parking area');
INSERT INTO amenity (amenity) VALUES ('wifi');
INSERT INTO amenity (amenity) VALUES ('vending machines');
INSERT INTO amenity (amenity) VALUES ('lake');
INSERT INTO amenity (amenity) VALUES ('docent');

