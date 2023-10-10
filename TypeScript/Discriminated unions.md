```tsx
type CommonProps = {
	pathArray: Array<{
		label: string;
		href?: string;
	}>;
	maxItems?: number | undefined;
	withBackButton: boolean;
}

type BreadcrumbsPropsWithBackButton = {
	withBackButton: true;
	backText: string;
	backLink: string;
}

type BreadcrumbsPropsWithoutBackButton = {
	withBackButton: false;
} 

type BreadcrumbsProps = CommonProps & (BreadcrumbsPropsWithBackButton | BreadcrumbsPropsWithoutBackButton);


const Breadcrumbs: FC<BreadcrumbsProps> = ({
	pathArray, maxItems, ...props
}) => (
	<Styled.Breadcrumbs maxItems={ maxItems }>
	// {...}   
	// props.backText i props.backLink dostępne są tylko po sprawdzeniu, czy withBackButton jest true 
    {
      props.withBackButton === true && (
        props.backText && (
          <Link href={ props.backLink }>
            {props.backText}
          </Link>
        )
      )
    }
  </Styled.Breadcrumbs>
);
```