---
title: Rozšíření značek připojení
ms.date: 03/30/2017
f1_keywords:
- Binding
helpviewer_keywords:
- Binding markup extensions [WPF]
- XAML [WPF], Binding markup extension
ms.assetid: 83d6e2a4-1b0c-4fc8-bd96-b5e98800ab63
ms.openlocfilehash: c6a424e085c7499db08d0a7e6b652f45fb2cdd70
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2020
ms.locfileid: "81644085"
---
# <a name="binding-markup-extension"></a>Rozšíření značek připojení
Odloží hodnotu vlastnosti jako hodnotu vázanou na data, vytvoří zprostředkující objekt výrazu a interpretuje kontext dat, který se vztahuje k prvku a jeho vazbě za běhu.  
  
## <a name="binding-expression-usage"></a>Použití výrazu vazby  
  
```xaml  
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
 V těchto syntaxe `[]` `*` a nejsou literály. Jsou součástí zápisu označující, že lze použít nula nebo více `,` párů*hodnot* *bindProp*`=`s oddělovačem mezi nimi a předchozími dvojicemi*hodnot* *bindProp.*`=`  
  
 Všechny vlastnosti uvedené v části "Vlastnosti vazby, které lze nastavit s rozšíření <xref:System.Windows.Data.Binding> mnoství vazby" místo toho lze nastavit pomocí atributů prvku objektu. To však není skutečně použití rozšíření <xref:System.Windows.Data.Binding>značky , je to pouze obecné xaml zpracování <xref:System.Windows.Data.Binding> atributů, které nastavují vlastnosti třídy CLR. Jinými slovy `<Binding` *bindProp1*`="`*value1* `"[` *bindPropN*`="`*valueN* `"]*/>` je ekvivalentní <xref:System.Windows.Data.Binding> syntaxe pro `Binding` atributy použití prvku objektu namísto použití výrazu. Informace o použití atributu XAML <xref:System.Windows.Data.Binding>konkrétních vlastností aplikace naleznete v části "Použití <xref:System.Windows.Data.Binding> atributů XAML" příslušné vlastnosti v knihovně tříd rozhraní .NET Framework.  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|`bindProp1, bindPropN`|Název vlastnosti <xref:System.Windows.Data.Binding> <xref:System.Windows.Data.BindingBase> nebo nastavit. Ne <xref:System.Windows.Data.Binding> všechny vlastnosti lze `Binding` nastavit s rozšířením a `Binding` některé vlastnosti jsou nastavitelné v rámci výrazu pouze pomocí dalších vnořených rozšíření značek. Viz "Vlastnosti vazby, které lze nastavit s rozšíření vazby" části.|  
|`value1, valueN`|Hodnota pro nastavení vlastnosti. Zpracování hodnoty atributu je nakonec specifické pro typ a <xref:System.Windows.Data.Binding> logiku konkrétní vlastnosti, která je nastavena.|  
|`path`|Řetězec cesty, který <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> nastaví implicitní vlastnost. Viz také [PropertyPath XAML Syntaxe](propertypath-xaml-syntax.md).|  
  
## <a name="unqualified-binding"></a>Neúplný {Vazba}  
 Použití `{Binding}` zobrazené v části "Použití <xref:System.Windows.Data.Binding> výrazu vazby" vytvoří <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> `null`objekt s výchozími hodnotami, který obsahuje iniciály . To je stále užitečné v mnoha <xref:System.Windows.Data.Binding> scénářích, protože vytvořené může <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> být <xref:System.Windows.Data.Binding.Source%2A?displayProperty=nameWithType> spoléhání se na vlastnosti klíče datové vazby, jako je například a jsou nastaveny v kontextu dat za běhu. Další informace o konceptu kontextu dat naleznete v tématu [Datové vazby](../../../desktop-wpf/data/data-binding-overview.md).  
  
## <a name="implicit-path"></a>Implicitní cesta  
 Rozšíření `Binding` značek používá <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> jako koncepční "výchozí vlastnost", kde `Path=` není nutné se objevit ve výrazu. Pokud zadáte `Binding` výraz s implicitní cestou, implicitní cesta se musí `bindProp` = `value` zobrazit nejprve <xref:System.Windows.Data.Binding> ve výrazu před ostatními páry, kde je vlastnost určena názvem. Například: `{Binding PathString}`, `PathString` kde je řetězec, který je <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> vyhodnocen jako hodnota v <xref:System.Windows.Data.Binding> použití rozšíření značky. K oddělovači čárky můžete připojit implicitní cestu s dalšími pojmenovanými vlastnostmi, `{Binding LastName, Mode=TwoWay}`například .  
  
## <a name="binding-properties-that-can-be-set-with-the-binding-extension"></a>Vlastnosti vazby, které lze nastavit s rozšířením vazby  
 Syntaxe zobrazená v tomto `bindProp` = `value` tématu používá obecnou aproximaci, <xref:System.Windows.Data.BindingBase> <xref:System.Windows.Data.Binding> protože existuje mnoho `Binding` vlastností pro čtení a zápis nebo které lze nastavit pomocí syntaxe rozšíření /výrazu značky. Mohou být nastaveny v libovolném pořadí, <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>s výjimkou implicitní . (Máte možnost explicitně zadat `Path=`, v takovém případě může být nastavena v libovolném pořadí). V podstatě můžete nastavit nulu nebo více vlastností `bindProp` = `value` v seznamu níže, pomocí párů oddělených čárkami.  
  
 Některé z těchto hodnot vlastností vyžadují typy objektů, které nepodporují převod nativního typu z syntaxe textu v jazyce XAML, a proto vyžadují rozšíření značek, aby bylo možné nastavit jako hodnotu atributu. Další informace naleznete v části Použití atributů XAML v knihovně tříd rozhraní .NET Framework pro každou vlastnost. řetězec, který použijete pro syntaxi atributu XAML s dalším použitím rozšíření značek `Binding` nebo bez něj, je v podstatě `bindProp` = `value` stejný `Binding` jako hodnota zadaná ve výrazu, s výjimkou, že neumístíte uvozovky kolem každého ve výrazu.  
  
- <xref:System.Windows.Data.BindingBase.BindingGroupName%2A>: řetězec, který identifikuje možnou skupinu vazeb. Jedná se o relativně pokročilý koncept vazby; viz referenční <xref:System.Windows.Data.BindingBase.BindingGroupName%2A>stránka pro .  
  
- <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A>: Boolean, může `true` `false`být buď nebo . Výchozí formát je `false`.  
  
- <xref:System.Windows.Data.Binding.Converter%2A>: lze nastavit `bindProp` = `value` jako řetězec ve výrazu, ale k tomu vyžaduje odkaz na objekt pro hodnotu, jako je například [StaticResource Markup Extension](staticresource-markup-extension.md). Hodnota v tomto případě je instancí třídy vlastní převaděč.  
  
- <xref:System.Windows.Data.Binding.ConverterCulture%2A>: nastavitelný ve výrazu jako identifikátor založený na standardech; viz referenční téma <xref:System.Windows.Data.Binding.ConverterCulture%2A>pro .  
  
- <xref:System.Windows.Data.Binding.ConverterParameter%2A>: lze nastavit `bindProp` = `value` jako řetězec ve výrazu, ale to závisí na typu předávaného parametru. Pokud předání typu odkazu pro hodnotu, toto použití vyžaduje odkaz na objekt, jako je například vnořené [StaticResource Markup Extension](staticresource-markup-extension.md).  
  
- <xref:System.Windows.Data.Binding.ElementName%2A>: vzájemně se <xref:System.Windows.Data.Binding.RelativeSource%2A> <xref:System.Windows.Data.Binding.Source%2A>vylučující versus a ; každá z těchto vlastností vazby představuje konkrétní metodiku vazby. Viz [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md).  
  
- <xref:System.Windows.Data.BindingBase.FallbackValue%2A>: lze nastavit `bindProp` = `value` jako řetězec ve výrazu, ale to závisí na typu předané hodnoty. Pokud předávání typu odkazu, vyžaduje odkaz na objekt, jako je například vnořené [StaticResource Markup Extension](staticresource-markup-extension.md).  
  
- <xref:System.Windows.Data.Binding.IsAsync%2A>: Boolean, může `true` `false`být buď nebo . Výchozí formát je `false`.  
  
- <xref:System.Windows.Data.Binding.Mode%2A>: *hodnota* je konstantní <xref:System.Windows.Data.BindingMode> název z výčtu. Například, `{Binding Mode=OneWay}`.  
  
- <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A>: Boolean, může `true` `false`být buď nebo . Výchozí formát je `false`.  
  
- <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A>: Boolean, může `true` `false`být buď nebo . Výchozí formát je `false`.  
  
- <xref:System.Windows.Data.Binding.NotifyOnValidationError%2A>: Boolean, může `true` `false`být buď nebo . Výchozí formát je `false`.  
  
- <xref:System.Windows.Data.Binding.Path%2A>: řetězec, který popisuje cestu do datového objektu nebo obecného objektového modelu. Formát poskytuje několik různých konvencí pro procházení objektového modelu, který nelze odpovídajícím způsobem popsat v tomto tématu. Viz [PropertyPath XAML Syntaxe](propertypath-xaml-syntax.md).  
  
- <xref:System.Windows.Data.Binding.RelativeSource%2A>: vzájemně se <xref:System.Windows.Data.Binding.ElementName%2A> vylučující proti a <xref:System.Windows.Data.Binding.Source%2A>; každá z těchto vlastností vazby představuje konkrétní metodiku vazby. Viz [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md). K určení hodnoty vyžaduje vnořené použití [služby RelativeSource MarkupExtension.](relativesource-markupextension.md)  
  
- <xref:System.Windows.Data.Binding.Source%2A>: vzájemně se <xref:System.Windows.Data.Binding.RelativeSource%2A> <xref:System.Windows.Data.Binding.ElementName%2A>vylučující versus a ; každá z těchto vlastností vazby představuje konkrétní metodiku vazby. Viz [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md). Vyžaduje vnořené využití rozšíření, obvykle [rozšíření StaticResource Markup Extension,](staticresource-markup-extension.md) které odkazuje na zdroj dat objektu z klíčového slovníku prostředků.  
  
- <xref:System.Windows.Data.BindingBase.StringFormat%2A>: řetězec, který popisuje konvenci formátu řetězce pro vázaná data. Jedná se o relativně pokročilý koncept vazby; viz referenční <xref:System.Windows.Data.BindingBase.StringFormat%2A>stránka pro .  
  
- <xref:System.Windows.Data.BindingBase.TargetNullValue%2A>: lze nastavit `bindProp` = `value` jako řetězec ve výrazu, ale to závisí na typu předávaného parametru. Pokud předání typu odkazu pro hodnotu, vyžaduje odkaz na objekt, jako je například vnořené [StaticResource Markup Extension](staticresource-markup-extension.md).  
  
- <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>: *hodnota* je konstantní <xref:System.Windows.Data.UpdateSourceTrigger> název z výčtu. Například, `{Binding UpdateSourceTrigger=LostFocus}`. Specifické ovládací prvky potenciálně mají různé výchozí hodnoty pro tuto vlastnost vazby. Viz třída <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.  
  
- <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A>: Boolean, může `true` `false`být buď nebo . Výchozí formát je `false`. Viz Poznámky.  
  
- <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A>: Boolean, může `true` `false`být buď nebo . Výchozí formát je `false`. Viz Poznámky.  
  
- <xref:System.Windows.Data.Binding.XPath%2A>: řetězec, který popisuje cestu do XMLDOM zdroje dat XML. Viz [Vazba na data XML pomocí dotazů XMLDataProvider a XPath](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).  
  
 Následují <xref:System.Windows.Data.Binding> vlastnosti, které nelze nastavit `Binding` pomocí formuláře`{Binding}` rozšíření/výrazu značky.  
  
- <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>: Tato vlastnost očekává odkaz na implementaci zpětného volání. Na zpětná volání/metody jiné než obslužné rutiny událostí nelze odkazovat v syntaxi XAML.  
  
- <xref:System.Windows.Data.Binding.ValidationRules%2A>: Vlastnost přebírá obecnou <xref:System.Windows.Controls.ValidationRule> kolekci objektů. To může být vyjádřeno jako <xref:System.Windows.Data.Binding> prvek vlastnosti v elementu objektu, ale nemá žádnou `Binding` snadno dostupnou techniku analýzy atributů pro použití ve výrazu. Viz referenční <xref:System.Windows.Data.Binding.ValidationRules%2A>téma pro .  
  
- <xref:System.Windows.Data.Binding.XmlNamespaceManager%2A>  
  
## <a name="remarks"></a>Poznámky  
  
> [!IMPORTANT]
> Z hlediska priority vlastnosti závislosti `Binding` je výraz ekvivalentní místně nastavené hodnotě. Pokud nastavíte místní hodnotu pro `Binding` vlastnost, `Binding` která dříve měla výraz, je zcela odebrána. Podrobnosti naleznete v [tématu Priorita hodnoty vlastnosti závislostí](dependency-property-value-precedence.md).  
  
 Popis datové vazby na základní úrovni není zahrnuta v tomto tématu. Viz [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md).  
  
> [!NOTE]
> <xref:System.Windows.Data.MultiBinding>a <xref:System.Windows.Data.PriorityBinding> nepodporují [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] syntaxi rozšíření. Místo toho byste použít prvky vlastnosti. Viz referenční <xref:System.Windows.Data.MultiBinding> témata <xref:System.Windows.Data.PriorityBinding>pro a .  
  
 Logické hodnoty pro XAML nerozlišují malá a velká písmena. Můžete například zadat `{Binding NotifyOnValidationError=true}` `{Binding NotifyOnValidationError=True}`buď nebo .  
  
 Vazby, které zahrnují ověření dat, `Binding` jsou obvykle určeny explicitním prvkem, nikoli jako `{Binding ...}` výraz, a nastavení <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> nebo <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> výraz je neobvyklé. Důvodem je, <xref:System.Windows.Data.Binding.ValidationRules%2A> že vlastnost companion nelze snadno nastavit ve formuláři výrazu. Další informace naleznete [v tématu Implementovat ověřování vazby](../data/how-to-implement-binding-validation.md).  
  
 `Binding`je rozšíření značky. Rozšíření značek jsou obvykle implementovány, pokud existuje požadavek na únik hodnoty atributů být jiné než literálové hodnoty nebo názvy obslužné rutiny a požadavek je globálnější než převaděče typu přiřazené na určité typy nebo vlastnosti. Všechna rozšíření značek v XAML `{` `}` používají znaky a v syntaxi jejich atributu, což je konvence, podle které procesor XAML rozpozná, že rozšíření značek musí zpracovat obsah řetězce. Další informace naleznete [v tématu Markup Extensions a WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
 `Binding`je atypické rozšíření značky <xref:System.Windows.Data.Binding> v tom, že třída, která implementuje funkci rozšíření pro implementaci WPF XAML také implementuje několik dalších metod a vlastností, které nesouvisejí s XAML. Ostatní členy jsou určeny k vytvoření <xref:System.Windows.Data.Binding> všestrannější a samostatné třídy, která může řešit mnoho scénářů datové vazby kromě fungování jako rozšíření značek XAML.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Data.Binding>
- [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md)
- [Přehled XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md)
