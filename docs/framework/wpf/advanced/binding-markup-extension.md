---
title: Rozšíření značek připojení
ms.date: 03/30/2017
f1_keywords:
- Binding
helpviewer_keywords:
- Binding markup extensions [WPF]
- XAML [WPF], Binding markup extension
ms.assetid: 83d6e2a4-1b0c-4fc8-bd96-b5e98800ab63
ms.openlocfilehash: 3455c7ccdedb432fc05c7dc9e80f0f7509f4fa0c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59170310"
---
# <a name="binding-markup-extension"></a>Rozšíření značek připojení
Odloží hodnotu vlastnosti bude hodnota vázané na data, vytvoření objektu zprostředkující výraz a interpretace kontext dat, která se vztahuje k elementu a jeho vazby v době běhu.  
  
## <a name="binding-expression-usage"></a>Použití výrazu vazby  
  
```  
<object property="{Binding}" .../>  
-or-  
<object property="{Binding  bindProp1=value1[, bindPropN=valueN]*}" ...  
/>  
-or-  
<object property="{Binding path}" .../>  
-or  
<object property="{Binding path[, bindPropN=valueN]*}" .../>  
```  
  
## <a name="syntax-notes"></a>Syntaxe poznámky  
 V těchto syntaxí `[]` a `*` nejsou literály. Jsou součástí zápis, která označuje, že nula nebo více *bindProp*`=`*hodnotu* páry je možné, s `,` oddělovač je a předchozí *bindProp*  `=` *hodnotu* dvojice.  
  
 Některé z vlastností uvedených v části "Vazby, může být nastaven s the vazby rozšíření vlastností" místo toho se dají nastavit pomocí atributů <xref:System.Windows.Data.Binding> elementu objektu. Ale to není skutečně použití rozšíření značky z <xref:System.Windows.Data.Binding>, jde jenom obecné XAML zpracování atributy, které nastavit vlastnosti CLR <xref:System.Windows.Data.Binding> třídy. Jinými slovy `<Binding` *bindProp1*`="`*hodnota1* `"[` *bindPropN*`="`*hodnotaN* `"]*/>` je ekvivalentní syntax pro atributy <xref:System.Windows.Data.Binding> objektu použití elementu namísto `Binding` použití výrazu. Další informace o použití atributu XAML konkrétních vlastností <xref:System.Windows.Data.Binding>, najdete v části "Použití atributu XAML" příslušné vlastnosti <xref:System.Windows.Data.Binding> v knihovně tříd rozhraní .NET Framework.  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|`bindProp1, bindPropN`|Název <xref:System.Windows.Data.Binding> nebo <xref:System.Windows.Data.BindingBase> vlastnosti chcete nastavit. Ne všechny <xref:System.Windows.Data.Binding> lze nastavit vlastnosti `Binding` rozšíření a některé vlastnosti je možné v rámci `Binding` výraz pouze s použitím dále vnořit – rozšíření značek. Viz část "Vazby, může být nastaven s the vazby rozšíření vlastností".|  
|`value1, valueN`|Hodnota pro vlastnost na hodnotu. Zpracování hodnota atributu je nakonec specifické pro typ a logiky konkrétní <xref:System.Windows.Data.Binding> vlastnost nastavena.|  
|`path`|Řetězec cesty, který nastaví implicitní <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> vlastnost. Viz také [syntaxe PropertyPath XAML](propertypath-xaml-syntax.md).|  
  
## <a name="unqualified-binding"></a>Nekvalifikované {vazba}  
 `{Binding}` Využití ukazuje využití výraz"vazba" vytvoří <xref:System.Windows.Data.Binding> objektu s výchozími hodnotami, které obsahuje počáteční <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> z `null`. Toto je stále užitečná v případech, protože vytvořený <xref:System.Windows.Data.Binding> mohou spoléhat na vlastnosti klíče datové vazby, jako <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> a <xref:System.Windows.Data.Binding.Source%2A?displayProperty=nameWithType> nastavena v kontextu dat za běhu. Další informace o konceptu kontext dat, naleznete v tématu [datové vazby](../data/data-binding-wpf.md).  
  
## <a name="implicit-path"></a>Implicitní cesta  
 `Binding` Používá rozšíření značek <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> jako koncepční "výchozí vlastnost", kde `Path=` nemusí zobrazovat ve výrazu. Pokud zadáte `Binding` výraz s implicitní cesta implicitní cesta musí být první ve výrazu, než jakýkoli jiný `bindProp` = `value` dvojice where <xref:System.Windows.Data.Binding> vlastnost je určena podle názvu. Příklad: `{Binding PathString}`, kde `PathString` je řetězec, který je vyhodnocen jako hodnota <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> v <xref:System.Windows.Data.Binding> vytvořené použití rozšíření značky. Implicitní cestu s další pojmenované vlastnosti můžete připojit za oddělovačem čárkou, například `{Binding LastName, Mode=TwoWay}`.  
  
## <a name="binding-properties-that-can-be-set-with-the-binding-extension"></a>Svázání vlastností, které lze nastavit pomocí rozšíření vazby  
 Obecné používá syntaxi uvedenou v tomto tématu `bindProp` = `value` sblížení, protože mnoho vlastností čtení/zápis <xref:System.Windows.Data.BindingBase> nebo <xref:System.Windows.Data.Binding> , které lze nastavit pomocí `Binding` – rozšíření značek / Syntaxe výrazu. To můžete udělat v libovolném pořadí, s výjimkou implicitní <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>. (Nutné explicitně zadat `Path=`, v takovém případě je možné nastavit v libovolném pořadí). V podstatě můžete nastavit nula nebo více vlastností v seznamu níže, pomocí `bindProp` = `value` páry oddělených čárkami.  
  
 Některé z těchto hodnot vlastností vyžadují typy objektů, které nepodporují nativní typ převodu ze syntaxe textu v XAML a proto potřebuje – rozšíření značek nastavit jako hodnotu atributu. Zkontrolujte v části použití atributu XAML v knihovně tříd rozhraní .NET Framework pro každou vlastnost pro další informace o; řetězec pomocí syntaxe XAML atribut s nebo bez další rozšíření značek použití je v podstatě stejný jako hodnotu zadáte `Binding` výrazu, s výjimkou Neumísťujte uvozovky kolem každé `bindProp` = `value` v `Binding` výrazu.  
  
-   <xref:System.Windows.Data.BindingBase.BindingGroupName%2A>: řetězec, který identifikuje skupinu vazeb. To je poměrně Rozšířená vazba koncept; najdete odkaz na stránce <xref:System.Windows.Data.BindingBase.BindingGroupName%2A>.  
  
-   <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A>: Logická hodnota, může být buď `true` nebo `false`. Výchozí hodnota je `false`.  
  
-   <xref:System.Windows.Data.Binding.Converter%2A>: můžete nastavit jako `bindProp` = `value` řetězec ve výrazu, ale k tomu vyžaduje odkaz na objekt pro hodnotu, například [– rozšíření značek StaticResource](staticresource-markup-extension.md). Hodnota v tomto případě je instance třídy vlastní převaděč.  
  
-   <xref:System.Windows.Data.Binding.ConverterCulture%2A>: nastavitelná při čekání ve výrazu jako identifikátor založené na standardech; Viz téma referenčních informací ke <xref:System.Windows.Data.Binding.ConverterCulture%2A>.  
  
-   <xref:System.Windows.Data.Binding.ConverterParameter%2A>: můžete nastavit jako `bindProp` = `value` řetězec ve výrazu, ale to je závislá na typ parametru předávána. Pokud předáváte odkaz na typ hodnoty, toto použití vyžaduje odkaz na objekt, jako je například vnořený [– rozšíření značek StaticResource](staticresource-markup-extension.md).  
  
-   <xref:System.Windows.Data.Binding.ElementName%2A>: vzájemně se vylučující oproti <xref:System.Windows.Data.Binding.RelativeSource%2A> a <xref:System.Windows.Data.Binding.Source%2A>; každý z nich svázání vlastností představuje metodologie konkrétní vazby. Zobrazit [datové vazby přehled](../data/data-binding-overview.md).  
  
-   <xref:System.Windows.Data.BindingBase.FallbackValue%2A>: můžete nastavit jako `bindProp` = `value` řetězec ve výrazu, ale to je závislá na typu zjištění předávané hodnoty. Pokud předávání typu odkazu, vyžaduje odkaz na objekt, jako je například vnořený [– rozšíření značek StaticResource](staticresource-markup-extension.md).  
  
-   <xref:System.Windows.Data.Binding.IsAsync%2A>: Logická hodnota, může být buď `true` nebo `false`. Výchozí hodnota je `false`.  
  
-   <xref:System.Windows.Data.Binding.Mode%2A>: *hodnotu* je konstantní název z <xref:System.Windows.Data.BindingMode> výčtu. Například, `{Binding Mode=OneWay}`.  
  
-   <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A>: Logická hodnota, může být buď `true` nebo `false`. Výchozí hodnota je `false`.  
  
-   <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A>: Logická hodnota, může být buď `true` nebo `false`. Výchozí hodnota je `false`.  
  
-   <xref:System.Windows.Data.Binding.NotifyOnValidationError%2A>: Logická hodnota, může být buď `true` nebo `false`. Výchozí hodnota je `false`.  
  
-   <xref:System.Windows.Data.Binding.Path%2A>: řetězec popisující cestu do datového objektu nebo obecný objektový model. Formát poskytuje několik různých konvencí k procházení objektový model, který nemůže být dostatečně popsané v tomto tématu. Zobrazit [syntaxe PropertyPath XAML](propertypath-xaml-syntax.md).  
  
-   <xref:System.Windows.Data.Binding.RelativeSource%2A>: porovnání vzájemně vylučuje s <xref:System.Windows.Data.Binding.ElementName%2A> a <xref:System.Windows.Data.Binding.Source%2A>; každý z nich svázání vlastností představuje konkrétní vazby metodologie. Zobrazit [datové vazby přehled](../data/data-binding-overview.md). Vyžaduje vnořený [rozšíření značek RelativeSource](relativesource-markupextension.md) informací o využití a zadejte hodnotu.  
  
-   <xref:System.Windows.Data.Binding.Source%2A>: vzájemně se vylučující oproti <xref:System.Windows.Data.Binding.RelativeSource%2A> a <xref:System.Windows.Data.Binding.ElementName%2A>; každý z nich svázání vlastností představuje metodologie konkrétní vazby. Zobrazit [datové vazby přehled](../data/data-binding-overview.md). Obvykle vyžaduje použití vnořeného rozšíření, [– rozšíření značek StaticResource](staticresource-markup-extension.md) , který odkazuje na zdroj dat objekt ze slovníku prostředků s klíči.  
  
-   <xref:System.Windows.Data.BindingBase.StringFormat%2A>: řetězec, který popisuje řetězec formátu konvence pro vázaným datům. To je poměrně Rozšířená vazba koncept; najdete odkaz na stránce <xref:System.Windows.Data.BindingBase.StringFormat%2A>.  
  
-   <xref:System.Windows.Data.BindingBase.TargetNullValue%2A>: můžete nastavit jako `bindProp` = `value` řetězec ve výrazu, ale to je závislá na typ parametru předávána. Pokud typ odkazu pro hodnotu předávání vyžaduje odkaz na objekt, jako je například vnořený [– rozšíření značek StaticResource](staticresource-markup-extension.md).  
  
-   <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>: *hodnotu* je konstantní název z <xref:System.Windows.Data.UpdateSourceTrigger> výčtu. Například, `{Binding UpdateSourceTrigger=LostFocus}`. Specifických kontrolních mechanismů můžou mít různé výchozí hodnoty pro tuto vlastnost vazby. Viz <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.  
  
-   <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A>: Logická hodnota, může být buď `true` nebo `false`. Výchozí hodnota je `false`. Viz poznámky.  
  
-   <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A>: Logická hodnota, může být buď `true` nebo `false`. Výchozí hodnota je `false`. Viz poznámky.  
  
-   <xref:System.Windows.Data.Binding.XPath%2A>: řetězec popisující cestu do XMLDOM zdroj dat XML. Zobrazit [připojení k datům XML použitím objektu XMLDataProvider a dotazů XPath](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).  
  
 Toto jsou vlastnosti <xref:System.Windows.Data.Binding> , který nelze nastavit pomocí `Binding` – rozšíření značek /`{Binding}` notace výrazu.  
  
-   <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>: Tato vlastnost očekává odkaz na implementaci zpětného volání. Zpětná volání nebo jiných metod než obslužné rutiny událostí se nedá odkazovat v syntaxe XAML.  
  
-   <xref:System.Windows.Data.Binding.ValidationRules%2A>: vlastnost má obecné kolekce <xref:System.Windows.Controls.ValidationRule> objekty. To může být vyjádřený jako prvek vlastnosti v <xref:System.Windows.Data.Binding> objekt elementu, ale nemá žádné snadno k dispozici techniku analýze atributu pro použití v `Binding` výrazu. Viz téma referenčních informací ke <xref:System.Windows.Data.Binding.ValidationRules%2A>.  
  
-   <xref:System.Windows.Data.Binding.XmlNamespaceManager%2A>  
  
## <a name="remarks"></a>Poznámky  
  
> [!IMPORTANT]
>  Z hlediska Priorita vlastností závislosti `Binding` výraz je ekvivalentní místně nastavené hodnoty. Pokud nastavíte hodnotu místní vlastnosti, které dříve měly `Binding` výrazu, `Binding` úplně Odebereme. Podrobnosti najdete v tématu [Priorita hodnot závislých vlastností](dependency-property-value-precedence.md).  
  
 V tomto tématu není uvedené popisující vytváření datových vazeb na základní úrovni. Zobrazit [datové vazby přehled](../data/data-binding-overview.md).  
  
> [!NOTE]
>  <xref:System.Windows.Data.MultiBinding> a <xref:System.Windows.Data.PriorityBinding> nepodporují [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] rozšíření syntaxe. Místo toho můžete využít prvcích vlastností. Najdete v referenčních tématech pro <xref:System.Windows.Data.MultiBinding> a <xref:System.Windows.Data.PriorityBinding>.  
  
 Logické hodnoty pro XAML jsou malá a velká písmena. Můžete třeba zadat buď `{Binding NotifyOnValidationError=true}` nebo `{Binding NotifyOnValidationError=True}`.  
  
 Vazby, které se týkají ověřování dat jsou obvykle určeny pomocí explicitní `Binding` element spíše než stejně jako `{Binding ...}` výrazu a nastavením <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> nebo <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> ve výrazu neobvyklé. Důvodem je, že vlastnost doprovodná <xref:System.Windows.Data.Binding.ValidationRules%2A> nelze snadno nastavit ve formě výrazu. Další informace najdete v tématu [implementace ověření vazby](../data/how-to-implement-binding-validation.md).  
  
 `Binding` je rozšíření značek. Rozšíření značek jsou obvykle implementována v případě požadavku k uvození atributu hodnoty jiné než literálními hodnotami nebo obslužná rutina názvy a požadavek je víc globálních než převaděčů typů pro určité typy nebo vlastnosti s atributy. Všechna rozšíření značek XAML používá `{` a `}` znaků v syntaxi atributu, což je konvence, podle kterého procesoru XAML rozpozná, že rozšíření značek musí zpracovat obsah řetězce. Další informace najdete v tématu [– rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
 `Binding` je rozšíření netypických kód, který <xref:System.Windows.Data.Binding> třídu, která implementuje funkce rozšíření pro WPF XAML implementace také implementuje několik metod a vlastností, které nesouvisí s XAML. Ujistěte se, mají ostatní členové <xref:System.Windows.Data.Binding> všestranný a samostatná třída, která může vyřešit řadu scénáře datových vazeb kromě funguje jako rozšíření značek XAML.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Data.Binding>
- [Přehled datových vazeb](../data/data-binding-overview.md)
- [Přehled XAML (WPF)](xaml-overview-wpf.md)
- [Rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md)
