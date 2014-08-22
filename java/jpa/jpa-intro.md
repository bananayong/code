# JPA

## Entities
* An entity is a lightweight persistence domain object
* 한 Entity는 DB에서 Table을 표현
* Entity 객체 하나는 DB에서 Row 한줄을 표현

### Requirements for Entity Classes
* javax.persistence.Entity로 어노테이션 되어야 한다.
* 클래스는 public or protected 그리고 기본생성자 필요
* class는 final이면 안된다. 메서드나 저장할 인스턴스 변수도 final이면 안된다.
* detached object 형태의 매개변수로 사용될려면, Serializable을 구현해야 한다.
* Entity가 아닌 클래스를 상속 받을수도 있고, Entity가 아닌 클래스가 상속할 수도 있다.
* 저장할 인스턴스 변수는 꼭 public이면 안되며, 엑세스 메서드나 비즈니스 메서드를 통해서만 접근 가능하다.

### Persistent Fields
* @Transient or trasient가 사용되지 않은 모든 필드는 영속 대상

### Using Collection
* Collection, Set, List, Map 사용가능
* 만약 Collection의 요소가 Basic type 또는 Embeddable class라면 @ElementCollcetion를 사용
* Map을 사용할 때, value가 기본타입 또는 Embeddable class라면 @ElementCollection, Entity라면 @OneToMany or @ManyToMany를 사용
* 양방향 관계에서 한 곳에서만 Map을 사용
* Map 키 타입이 Entity일때, @MapKeyJoinColumn 사용, 만약 여러 컬럼이 필요하면, @MapKeyJoinColumns를 사용
* 만약 Map 키가 Value의 primary key 또는 필드라면 @MapKey사용, @MapKeyClass와 @MapKey는 동시에 사용될 수 없다.
* Value가 Entity인 단방향 OneToMany관계에서는 @JoinColumn 사용

### Primary keys in Entities
* @Id 이용
* 복합키는 @EmbeddedId 또는 @IdClass 사용

### Primary key class requirements
* key class는 public
* propertys는 public or protected
* 기본생성자
* hashcode equals 구현
* serilizable 구현

### Bidirectional Relationships
* inverse side에서 owning side에 대한 mappedBy를 표시해야한다.
* manyToOne에서 many side는 mappedBy 사용하지 않음, many side는 항상 관계에서 owning side
* oneToOne에서 외래키를 가지는 쪽이 owning side
* manyToMany에서는 양쪽 모두 owning side가 될 수 있음

### Cascade Operation for Entities
* ALL - DETACH, MERGE, PERSIST, REFRESH, REMOVE
* DETACH
* MERGE
* PERSIST
* REFRESH
* REMOVE
* orphanRemovel attribute of OneToMnay, OneToOne

### Embeddable Class in Entities
* @Embeddable, @Embeddeb 사용
* @Entity 사용하지 않음, id가 없음


-----------------------

## Entity Inheritance
### Entity inheritance Mapping strategies
* 상속 구조당 테이블 1개
* 구현 클래스당 테이블 1개
* Join 전략
* InheritanceType - SINGLE\_TABLE, JOINED, TABLE\_PER\_CLASS

### Single Table
* @DiscriminatorColumn이 존재
* @DiscriminatorValue를 이용하여 Entity 구분
* 다형관계 잘 지원, 전체 엔티티를 조회하는 쿼리가 가능
* 추가적인 컬럼이 필요

### The Table per Concrete Class Strategy
* 다형관계 지원이 좋지 않음, 여러 엔티티 조회시 UNION이나 분리된 쿼리가 사용됨
* JPA 벤더가 지원하지 않을 수도 있음. glassfish 안함

### The Joined Subclass Strategy
* 최상위 부모 테이블 존재
* 하위 클래스마다 테이블 존재
* 다형 관계 잘 지원
* Join을 많이 사용하여 성능저하를 가져올수 있음
* 추가 컬럼이 필요

## Managing Entities
### Managing an Entity Instance's Lifecyle
* new, managed, detached, removed

## DataBase Scheme Creation
### Configuring an Application to create or drop database tables
* none
* create
* drop-and-create
* drop