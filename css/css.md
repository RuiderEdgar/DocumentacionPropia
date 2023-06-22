# Estilos css

## Para imagenes de fondo

background: linear-gradient(rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.5)), url('') no-repeat center / cover

- no-repeat: para no repetir la imagen de fondo
- cover: para que se adapte al tamaño de la pantalla
- linear-gradient: para darle un filtro del color oscuro

Para hacer el fondo de la imagen difuminada hacia un color
	linear-gradient(0deg, #003641 8.65%, rgba(27, 127, 131, 0) 100%)


## Tamaño de letras para responsive

:root {
    /*font size for html = fontsize 62.5%*/
    --smallest: 1.2rem;
    --details: 1.3rem;
    /*up to 1.4 or 14px*/
    --body-text: 1.6rem;
    /*up to 1.8 or 18px*/
    --subtitle: 1.8rem;
    /*up to 2.0*/
    --title: 2.4rem;
    /*up to 2.8*/
    --header: 3.2rem;
    /*up to 3.8*/
}

@media (min-width: 768px) {
     :root {
        --smallest: 1.6rem;
        --details: 1.6rem;
        /*up to 1.8 or 18px*/
        --body-text: 2rem;
        /*up to 2.1 or 21px*/
        --subtitle: 2.1rem;
        /*up to 2.4*/
        --title: 3.4rem;
        /*up to 3.8*/
        --header: 4rem;
        /*up to 4.8*/
    }
}

## Responsive

	@media (min-width: 768px) and (max-width: 992px) {
	}
	@media (min-width: 993px) and (max-width: 1199px) {
	}
	@media (min-width: 1200px) {
	}
