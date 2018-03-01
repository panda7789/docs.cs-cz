---
title: "Rozšíření značek připojení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Binding
helpviewer_keywords:
- Binding markup extensions [WPF]
- XAML [WPF], Binding markup extension
ms.assetid: 83d6e2a4-1b0c-4fc8-bd96-b5e98800ab63
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: cc6a0616c6b462ffe6aca0a9adf27ac2ac7b7828
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="binding-markup-extension"></a>Rozšíření značek připojení
Odkládat údaje hodnotu vlastnosti na hodnotu vázané na data, vytvoření objektu zprostředkující výraz a interpretace kontextu dat, která se vztahuje k elementu a jeho vazby v době běhu.  
  
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
  
## <a name="syntax-notes"></a>Poznámky k syntaxi  
 V těchto syntaxí `[]` a `*` nejsou literály. Jsou součástí zápis, která označuje, že nula nebo více *bindProp*`=`*hodnotu* páry je možné použít s `,` oddělovače mezi je a předchozí *bindProp*  `=` *hodnotu* páry.  
  
 Některé z vlastností uvedených v části "Vytvoření vazby, může být nastavit s vazby rozšíření vlastností" může místo toho nastavit pomocí atributů <xref:System.Windows.Data.Binding> object element. Ale, který není skutečně použití rozšíření značek <xref:System.Windows.Data.Binding>, je právě obecné XAML zpracování atributy, které nastavit vlastnosti CLR <xref:System.Windows.Data.Binding> třídy. Jinými slovy `<Binding` *bindProp1*`="`*value1* `"[` *bindPropN*`="`*hodnotaN* `"]*/>` je ekvivalentní syntaxe pro atributy <xref:System.Windows.Data.Binding> objektu použití elementu místo `Binding` využití výraz. Další informace o použití atributu XAML konkrétní vlastnosti <xref:System.Windows.Data.Binding>, najdete v části "Použití atributu XAML" relevantní vlastnosti <xref:System.Windows.Data.Binding> v knihovně tříd rozhraní .NET Framework.  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|`bindProp1, bindPropN`|Název <xref:System.Windows.Data.Binding> nebo <xref:System.Windows.Data.BindingBase> vlastnost nastavit. Ne všechny <xref:System.Windows.Data.Binding> můžete nastavit vlastnosti `Binding` rozšíření a některé vlastnosti jsou nastavit v rámci `Binding` výraz pouze na základě další vnořené rozšíření značek. Informace v části "Vytvoření vazby, může být nastavit s vazby rozšíření vlastností".|  
|`value1, valueN`|Hodnota k nastavení vlastnosti. Zpracování hodnoty atributu se nakonec specifické pro typ a logiku konkrétní <xref:System.Windows.Data.Binding> vlastnost nastavena.|  
|`path`|Řetězec cesty, která nastavuje implicitní <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> vlastnost. Viz také [syntaxe PropertyPath XAML](../../../../docs/framework/wpf/advanced/propertypath-xaml-syntax.md).|  
  
## <a name="unqualified-binding"></a>Nekvalifikované {vazba}  
 `{Binding}` Vytvoří využití ukazuje "Vazby využití výraz" <xref:System.Windows.Data.Binding> objektu s výchozími hodnotami, které zahrnují počáteční <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> z `null`. Toto je stále užitečné v případech, protože vytvořený <xref:System.Windows.Data.Binding> může spoléhat na vlastnosti vazby klíčová data, jako <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> a <xref:System.Windows.Data.Binding.Source%2A?displayProperty=nameWithType> se nastavuje v kontextu spuštění data. Další informace o konceptu kontextu dat najdete v tématu [datové vazby](../../../../docs/framework/wpf/data/data-binding-wpf.md).  
  
## <a name="implicit-path"></a>Implicitní cesta  
 `Binding` Používá rozšíření značek <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> jako koncepční "výchozí vlastnost", kde `Path=` nemusí zobrazovat ve výrazu. Pokud zadáte `Binding` výraz s implicitní cesta implicitní cesta musí být nejdříve uveden v výraz před všemi ostatními `bindProp` = `value` páry where <xref:System.Windows.Data.Binding> vlastnost je určena podle názvu. Příklad: `{Binding PathString}`, kde `PathString` je řetězec, který je vyhodnocena jako hodnota <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> v <xref:System.Windows.Data.Binding> vytvořené využití rozšíření značek. Cesta k implicitní s další pojmenovaných vlastností můžete připojit za oddělovačem čárkami, například `{Binding LastName, Mode=TwoWay}`.  
  
## <a name="binding-properties-that-can-be-set-with-the-binding-extension"></a>Vlastnosti vazby, které lze nastavit s příponou vazby  
 Obecná používá syntaxi uvedenou v tomto tématu `bindProp` = `value` sblížení, protože nejsou k dispozici mnoho vlastností čtení/zápisu <xref:System.Windows.Data.BindingBase> nebo <xref:System.Windows.Data.Binding> je možné nastavit prostřednictvím `Binding` – rozšíření značek / Syntaxe výrazu. Lze nastavit v libovolném pořadí, s výjimkou implicitní <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>. (Nutné explicitně zadat `Path=`, v takovém případě může být nastavena v libovolném pořadí). V podstatě, můžete nastavit nula nebo více vlastností v seznamu, pomocí `bindProp` = `value` páry oddělených čárkami.  
  
 Některé z těchto hodnot vlastností vyžadují typy objektů, které nepodporují nativní typ převodu z syntaxe text v jazyce XAML a proto potřebuje rozšíření značek k být nastavená jako hodnota atributu. Zkontrolujte části použití atributu XAML v knihovně tříd rozhraní .NET Framework pro každou vlastnost informace; řetězec pomocí syntaxe jazyka XAML atribut s nebo bez další – rozšíření značek využití je v podstatě stejný jako hodnota zadaná v `Binding` výrazu, s výjimkou Neumísťujte uvozovky každý `bindProp` = `value` v `Binding` výraz.  
  
-   <xref:System.Windows.Data.BindingBase.BindingGroupName%2A>: řetězec, který identifikuje skupinu možných vazby. Toto je poměrně pokročilé vazby koncept; Viz stránka s referencemi pro <xref:System.Windows.Data.BindingBase.BindingGroupName%2A>.  
  
-   <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A>: Logická hodnota, může být buď `true` nebo `false`. Výchozí hodnota je `false`.  
  
-   <xref:System.Windows.Data.Binding.Converter%2A>: můžete nastavit jako `bindProp` = `value` řetězec ve výrazu, ale k tomu vyžaduje odkaz na objekt pro hodnotu, jako například [StaticResource – rozšíření značek](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md). Hodnota v tomto případě je instance třídy vlastní převaděč.  
  
-   <xref:System.Windows.Data.Binding.ConverterCulture%2A>: nastavit ve výrazu jako identifikátor založených na standardech; najdete v tématu o <xref:System.Windows.Data.Binding.ConverterCulture%2A>.  
  
-   <xref:System.Windows.Data.Binding.ConverterParameter%2A>: můžete nastavit jako `bindProp` = `value` řetězec v výraz, ale to je závislá na typ parametru předávány. Pokud předávání typu odkazu pro hodnotu, toto použití vyžaduje odkaz na objekt, jako je například vnořený [StaticResource – rozšíření značek](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md).  
  
-   <xref:System.Windows.Data.Binding.ElementName%2A>: vzájemně se vylučuje versus <xref:System.Windows.Data.Binding.RelativeSource%2A> a <xref:System.Windows.Data.Binding.Source%2A>; každý z těchto vazby vlastnosti představuje metodika konkrétní vazby. V tématu [datové vazby přehled](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
-   <xref:System.Windows.Data.BindingBase.FallbackValue%2A>: můžete nastavit jako `bindProp` = `value` řetězec v výraz, ale to je závislá na typ hodnoty předávány. Pokud předávání typu odkazu vyžaduje odkaz na objekt, jako je například vnořený [StaticResource – rozšíření značek](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md).  
  
-   <xref:System.Windows.Data.Binding.IsAsync%2A>: Logická hodnota, může být buď `true` nebo `false`. Výchozí hodnota je `false`.  
  
-   <xref:System.Windows.Data.Binding.Mode%2A>: *hodnotu* konstantní název z <xref:System.Windows.Data.BindingMode> výčtu. Například `{Binding Mode=OneWay}`.  
  
-   <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A>: Logická hodnota, může být buď `true` nebo `false`. Výchozí hodnota je `false`.  
  
-   <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A>: Logická hodnota, může být buď `true` nebo `false`. Výchozí hodnota je `false`.  
  
-   <xref:System.Windows.Data.Binding.NotifyOnValidationError%2A>: Logická hodnota, může být buď `true` nebo `false`. Výchozí hodnota je `false`.  
  
-   <xref:System.Windows.Data.Binding.Path%2A>: řetězec, který popisuje cestu do objekt dat nebo obecné objektový model. Formát poskytuje několik různých pravidel pro procházení objektový model, který nemůže být adekvátní popsaných v tomto tématu. V tématu [syntaxe PropertyPath XAML](../../../../docs/framework/wpf/advanced/propertypath-xaml-syntax.md).  
  
-   <xref:System.Windows.Data.Binding.RelativeSource%2A>: vzájemně se vylučuje porovnání s <xref:System.Windows.Data.Binding.ElementName%2A> a <xref:System.Windows.Data.Binding.Source%2A>; každý z těchto vazby vlastnosti představuje metodika konkrétní vazby. V tématu [datové vazby přehled](../../../../docs/framework/wpf/data/data-binding-overview.md). Vyžaduje vnořený [RelativeSource MarkupExtension](../../../../docs/framework/wpf/advanced/relativesource-markupextension.md) využití zadejte hodnotu.  
  
-   <xref:System.Windows.Data.Binding.Source%2A>: vzájemně se vylučuje versus <xref:System.Windows.Data.Binding.RelativeSource%2A> a <xref:System.Windows.Data.Binding.ElementName%2A>; každý z těchto vazby vlastnosti představuje metodika konkrétní vazby. V tématu [datové vazby přehled](../../../../docs/framework/wpf/data/data-binding-overview.md). Obvykle vyžaduje použití vnořených rozšíření [StaticResource – rozšíření značek](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) který odkazuje na zdroj dat objekt ze slovníku s klíčem prostředků.  
  
-   <xref:System.Windows.Data.BindingBase.StringFormat%2A>: řetězec, který popisuje konvence pro vázaný datový formát řetězce. Toto je poměrně pokročilé vazby koncept; Viz stránka s referencemi pro <xref:System.Windows.Data.BindingBase.StringFormat%2A>.  
  
-   <xref:System.Windows.Data.BindingBase.TargetNullValue%2A>: můžete nastavit jako `bindProp` = `value` řetězec v výraz, ale to je závislá na typ parametru předávány. Pokud předávání typu odkazu pro hodnotu, vyžaduje odkaz na objekt, jako je například vnořený [StaticResource – rozšíření značek](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md).  
  
-   <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>: *hodnotu* konstantní název z <xref:System.Windows.Data.UpdateSourceTrigger> výčtu. Například `{Binding UpdateSourceTrigger=LostFocus}`. Konkrétní ovládací prvky můžou mít různé výchozí hodnoty pro tuto vlastnost vazby. V tématu <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.  
  
-   <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A>: Logická hodnota, může být buď `true` nebo `false`. Výchozí hodnota je `false`. V části poznámky.  
  
-   <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A>: Logická hodnota, může být buď `true` nebo `false`. Výchozí hodnota je `false`. V části poznámky.  
  
-   <xref:System.Windows.Data.Binding.XPath%2A>: řetězec, který popisuje cestu do XMLDOM zdroje dat XML. V tématu [vazby na Data XML pomocí XMLDataProvider a dotazy jazyka XPath](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).  
  
 Toto jsou vlastnosti <xref:System.Windows.Data.Binding> , se nedají nastavit pomocí `Binding` – rozšíření značek /`{Binding}` výraz formuláře.  
  
-   <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>: Tato vlastnost očekává odkaz na implementaci zpětného volání. Zpětná volání nebo jiných metod než obslužné rutiny událostí nelze odkazovat v syntaxi jazyka XAML.  
  
-   <xref:System.Windows.Data.Binding.ValidationRules%2A>: vlastnost přijímá obecné kolekce <xref:System.Windows.Controls.ValidationRule> objekty. To může být vyjádřený jako vlastnost prvek, <xref:System.Windows.Data.Binding> objekt elementu, ale nemá žádné snadno dostupné analýza atribut technika pro použití v `Binding` výraz. Viz téma je referencí pro <xref:System.Windows.Data.Binding.ValidationRules%2A>.  
  
-   <xref:System.Windows.Data.Binding.XmlNamespaceManager%2A>  
  
## <a name="remarks"></a>Poznámky  
  
> [!IMPORTANT]
>  Z hlediska přednost před vlastností závislostí `Binding` výraz je ekvivalentní místně nastavte hodnotu. Pokud nastavíte místní hodnotu pro vlastnost, která dřív měla `Binding` výrazu `Binding` je zcela odebrána. Podrobnosti najdete v tématu [přednost hodnota vlastnosti závislosti](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md).  
  
 Datová vazba na základní úrovni popisující není zahrnutý v tomto tématu. V tématu [datové vazby přehled](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
> [!NOTE]
>  <xref:System.Windows.Data.MultiBinding>a <xref:System.Windows.Data.PriorityBinding> nepodporují [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] rozšíření syntaxe. Místo toho použijte vlastnost elementy. V tématu referenční témata pro <xref:System.Windows.Data.MultiBinding> a <xref:System.Windows.Data.PriorityBinding>.  
  
 Hodnoty Boolean pro jazyk XAML se malá a velká písmena. Můžete například zadat buď `{Binding NotifyOnValidationError=true}` nebo `{Binding NotifyOnValidationError=True}`.  
  
 Vazby, které zahrnují ověření dat jsou obvykle určené explicitního `Binding` element spíš než jako `{Binding ...}` výraz a nastavení <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> nebo <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> ve výrazu neobvyklé. Důvodem je, že vlastnost doprovodné <xref:System.Windows.Data.Binding.ValidationRules%2A> nelze snadno nastavit ve formuláři výraz. Další informace najdete v tématu [ověření vazby implementace](../../../../docs/framework/wpf/data/how-to-implement-binding-validation.md).  
  
 `Binding`je rozšíření značek. Rozšíření značek jsou obvykle implementované při požadavku, abyste se vyhnuli hodnoty atributu být než literálových hodnot nebo obslužná rutina názvy a požadavek je globální více než převaděčů typů s atributy na určité typy nebo vlastnosti. Všechna rozšíření značek v XAML použití `{` a `}` znaků v jejich syntaxi atributů, což je konvence, podle kterého XAML procesor rozpozná, že rozšíření značek musí zpracovat obsahu řetězce. Další informace najdete v tématu [rozšíření značek a WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
 `Binding`je v tom, že rozšíření netypických značek <xref:System.Windows.Data.Binding> třídu, která implementuje funkce rozšíření pro implementaci XAML pro WPF také implementuje několik dalších metod a vlastností, které nesouvisí se XAML. Jiní členové jsou určené aby <xref:System.Windows.Data.Binding> více univerzální a nezávislý třídu, která může vyřešit mnoho scénáře datových vazeb kromě funguje jako rozšíření značek XAML.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Data.Binding>  
 [Přehled datových vazeb](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Přehled XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Rozšíření značek a WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
