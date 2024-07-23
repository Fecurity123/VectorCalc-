use std::fmt;

#[derive(Debug, Clone)]
struct Vector {
    components: Vec<f64>,
}

impl Vector {
  
    fn new(components: Vec<f64>) -> Self {
        Vector { components }
    }

   
    fn check_dimension(&self, other: &Vector) -> Result<(), &'static str> {
        if self.components.len() != other.components.len() {
            Err("Векторы имеют разные размерности")
        } else {
            Ok(())
        }
    }

  
    fn add(&self, other: &Vector) -> Result<Vector, &'static str> {
        self.check_dimension(other)?;
        let components = self.components.iter()
            .zip(&other.components)
            .map(|(a, b)| a + b)
            .collect();
        Ok(Vector::new(components))
    }

    
    fn subtract(&self, other: &Vector) -> Result<Vector, &'static str> {
        self.check_dimension(other)?;
        let components = self.components.iter()
            .zip(&other.components)
            .map(|(a, b)| a - b)
            .collect();
        Ok(Vector::new(components))
    }

  
    fn dot_product(&self, other: &Vector) -> Result<f64, &'static str> {
        self.check_dimension(other)?;
        let result = self.components.iter()
            .zip(&other.components)
            .map(|(a, b)| a * b)
            .sum();
        Ok(result)
    }
}


impl fmt::Display for Vector {
    fn fmt(&self, f: &mut fmt::Formatter<'_>) -> fmt::Result {
        write!(f, "[{}]", self.components.iter().map(|x| x.to_string()).collect::<Vec<_>>().join(", "))
    }
}

fn main() {
    let v1 = Vector::new(vec![1.0, 2.0, 3.0]);
    let v2 = Vector::new(vec![4.0, 5.0, 6.0]);

    match v1.add(&v2) {
        Ok(result) => println!("Сложение: {}", result),
        Err(e) => println!("Ошибка: {}", e),
    }

    match v1.subtract(&v2) {
        Ok(result) => println!("Вычитание: {}", result),
        Err(e) => println!("Ошибка: {}", e),
    }

    match v1.dot_product(&v2) {
        Ok(result) => println!("Скалярное произведение: {}", result),
        Err(e) => println!("Ошибка: {}", e),
    }
}
