![alt text](https://raw.githubusercontent.com/ossgroupp/react-image/HEAD/media/logo.png 'An illustration of an atom')

# React Srcset Images for OSSPIM

A React package to output an img tag with different source variations from OSSPIM using srcset. Use this to easily build responsive images powered by the [OSSPIM headless commerce service](https://ossgroup.com/).

And don't forget:
[react image sizes attribute for fast ecommerce](https://ossgroup.com/blog/react-image-sizes-attribute-for-fast-ecommerce).

## Demo

[Demo](https://react-image.milliseconds.io/)

## Install

```
yarn add @osspim/react-image
```

## Use

```
import { Image } from '@osspim/react-image';

const imageFromOSSPIM = {
    url: '...',
    variants: [...]
}

<Image
    {...imageFromOSSPIM}
    sizes="(max-width: 700px) 90vw, 700px"
/>
```

## Render child function

```
const imageFromOSSPIM = {
    url: '...',
    variants: [...],
    altText: ''
}

<Image
    {...imageFromOSSPIM}
    sizes="(max-width: 700px) 90vw, 700px"
>
  {({
      src,
      srcSet,
      srcSetWebp,
      useAvif,
      useWebP,
      sizes,
      width,
      height,
      loading,
      alt,
      originalFileExtension,
      ...rest
    }) => {
      // Roll your own render
      return (
          <picture {...rest}>
            {useAvif && (
                <source srcSet={srcSetAvif} type="image/avif" sizes={sizes} />
            )}
            {useWebP && (
                <source srcSet={srcSetWebp} type="image/webp" sizes={sizes} />
            )}
            {srcSet.length > 0 && (
                <source
                    srcSet={srcSet.join(", ")}
                    src={std[0].url}
                    type={`image/${originalFileExtension}`}
                    sizes={sizes}
                />
            )}

            <img src={src} width={width} height={height} loading={loading} alt={alt} />
        </picture>
      )
  }}
</Image>
```
# react-image
