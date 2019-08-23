---
title: Rozšíření značek připojení
ms.date: 03/30/2017
f1_keywords:
- Binding
helpviewer_keywords:
- Binding markup extensions [WPF]
- XAML [WPF], Binding markup extension
ms.assetid: 83d6e2a4-1b0c-4fc8-bd96-b5e98800ab63
ms.openlocfilehash: 616e405e191cb264a002e903bed60cf04559a675
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964904"
---
# <a name="binding-markup-extension"></a>Rozšíření značek připojení
Odloží hodnotu vlastnosti na hodnotu vázanou na data, vytvoří objekt mezilehlého výrazu a interpretuje datový kontext, který se vztahuje na element a jeho vazbu v době běhu.  
  
## <a name="binding-expression-usage"></a>Použití výrazů vazby  
  
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
 V těchto syntaxech, `[]` a `*` nejsou literály. Jsou součástí zápisu, který označuje, že je `,` možné použít nula nebo více párů *bindProp*`=`*hodnot* s oddělovačem mezi nimi a předchozími páry *bindProp*`=`*hodnoty* .  
  
 Některé z vlastností uvedených v části "vlastnosti vazby, které lze nastavit pomocí rozšíření vazby", lze nastavit pomocí atributů <xref:System.Windows.Data.Binding> elementu Object. To však není ve skutečnosti použití <xref:System.Windows.Data.Binding>rozšíření značek, je to pouze obecné zpracování XAML atributů, které nastavují vlastnosti třídy CLR. <xref:System.Windows.Data.Binding> Jinými `<Binding` slovy, *bindProp1*`="`*hodnota1* *bindPropN valueN* je ekvivalentní Syntax pro atributy<xref:System.Windows.Data.Binding>použitíelementuObject. `"]*/>` `="``"[` místo použití výrazu `Binding` . Další informace o použití atributů XAML specifických vlastností pro <xref:System.Windows.Data.Binding>naleznete v části "použití atributu XAML" v příslušné <xref:System.Windows.Data.Binding> vlastnosti v knihovně tříd .NET Framework.  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|`bindProp1, bindPropN`|Název <xref:System.Windows.Data.Binding> vlastnosti nebo <xref:System.Windows.Data.BindingBase> , která se má nastavit. Ne všechny <xref:System.Windows.Data.Binding> vlastnosti lze nastavit `Binding` s příponou a některé `Binding` vlastnosti lze nastavit v rámci výrazu pouze pomocí dalších vnořených rozšíření značek. Viz část "vlastnosti vazby, které lze nastavit pomocí rozšíření vazby".|  
|`value1, valueN`|Hodnota, na kterou má být vlastnost nastavena. Zpracování hodnoty atributu je nakonec specifické pro typ a logiku nastavené konkrétní <xref:System.Windows.Data.Binding> vlastnosti.|  
|`path`|Řetězec cesty, který nastavuje vlastnost implicitní <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> . Viz také [PROPERTYPATH XAML Syntax](propertypath-xaml-syntax.md).|  
  
## <a name="unqualified-binding"></a>Nekvalifikované {Binding}  
 Použití zobrazené v "použití výrazu vazby" <xref:System.Windows.Data.Binding> vytvoří objekt s výchozími hodnotami, `null`které obsahují počáteční <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> hodnotu. `{Binding}` To je stále užitečné v mnoha scénářích, protože vytvořené <xref:System.Windows.Data.Binding> se můžou spoléhat na vlastnosti <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> vazby dat klíčů, jako je a <xref:System.Windows.Data.Binding.Source%2A?displayProperty=nameWithType> nastavovaná v kontextu dat za běhu. Další informace o konceptu kontextu dat najdete v tématu [datové vazby](../data/data-binding-wpf.md).  
  
## <a name="implicit-path"></a>Implicitní cesta  
 Rozšíření značek používá <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> jako koncepční "výchozí vlastnost", kde `Path=` se nemusí ve výrazu vyskytovat. `Binding` Pokud `Binding` zadáte výraz s implicitní cestou, implicitní cesta musí být nejprve ve výrazu, před všemi ostatními `value` `bindProp` = páry, kde <xref:System.Windows.Data.Binding> je vlastnost určena podle názvu. Například: `{Binding PathString}`, kde `PathString` je řetězec, který je vyhodnocen jako hodnota <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> v poli <xref:System.Windows.Data.Binding> vytvořeném použitím rozšíření značek. Můžete připojit implicitní cestu k ostatním pojmenovaným vlastnostem za oddělovačem čárky, například `{Binding LastName, Mode=TwoWay}`.  
  
## <a name="binding-properties-that-can-be-set-with-the-binding-extension"></a>Vlastnosti vazby, které lze nastavit pomocí rozšíření vazby  
 Syntaxe zobrazená v tomto tématu používá obecnou `bindProp` <xref:System.Windows.Data.Binding> = `value` aproximaci, protože <xref:System.Windows.Data.BindingBase> existuje mnoho vlastností pro čtení/zápis nebo, které lze nastavit prostřednictvím `Binding` rozšíření značek/ syntaxe výrazu Lze je nastavit v libovolném pořadí, s výjimkou implicitního <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>. (Máte možnost explicitně zadat `Path=`, v takovém případě ji lze nastavit v libovolném pořadí). V podstatě můžete nastavit nula nebo více vlastností v seznamu níže a použít `bindProp` = `value` páry oddělené čárkami.  
  
 Některé z těchto hodnot vlastností vyžadují typy objektů, které nepodporují převod nativního typu z syntaxe textu v jazyce XAML, a proto vyžadují rozšíření značek, aby je bylo možné nastavit jako hodnotu atributu. Další informace najdete v části použití atributů XAML v knihovně tříd .NET Framework pro každou vlastnost. řetězec, který použijete pro syntaxi atributů XAML s nebo bez dalšího použití rozšíření značek, je v podstatě stejný jako hodnota, kterou zadáte `Binding` ve výrazu, s výjimkou, že kolem každého `bindProp` =neumísťujeuvozovky.vevýrazu. `value` `Binding`  
  
- <xref:System.Windows.Data.BindingBase.BindingGroupName%2A>: řetězec, který identifikuje možnou skupinu vazeb. Toto je poměrně pokročilý koncept vazby; viz Referenční stránka pro <xref:System.Windows.Data.BindingBase.BindingGroupName%2A>.  
  
- <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A>: Logická hodnota, může být `true` buď `false`nebo. Výchozí hodnota je `false`.  
  
- <xref:System.Windows.Data.Binding.Converter%2A>: dá se `bindProp` nastavit jako = `value` řetězec ve výrazu, ale pokud to uděláte, vyžaduje odkaz na objekt pro tuto hodnotu, jako je například [rozšíření značek StaticResource](staticresource-markup-extension.md). Hodnota v tomto případě je instancí vlastní třídy převaděče.  
  
- <xref:System.Windows.Data.Binding.ConverterCulture%2A>: nastavit ve výrazu jako identifikátor založený na standardech; Viz referenční téma pro <xref:System.Windows.Data.Binding.ConverterCulture%2A>.  
  
- <xref:System.Windows.Data.Binding.ConverterParameter%2A>: lze nastavit jako `bindProp` = `value` řetězec ve výrazu, ale je závislý na typu předávaného parametru. Při předání typu odkazu pro hodnotu toto použití vyžaduje odkaz na objekt, jako je například vnořená [přípona značek StaticResource](staticresource-markup-extension.md).  
  
- <xref:System.Windows.Data.Binding.ElementName%2A>: vzájemně se <xref:System.Windows.Data.Binding.RelativeSource%2A> vylučují <xref:System.Windows.Data.Binding.Source%2A>oproti a; každá z těchto vlastností vazby představuje konkrétní metodologii vazby. Viz [Přehled datové vazby](../data/data-binding-overview.md).  
  
- <xref:System.Windows.Data.BindingBase.FallbackValue%2A>: lze nastavit jako `bindProp` = `value` řetězec ve výrazu, ale je závislý na typu předávané hodnoty. Při předání typu odkazu vyžaduje odkaz na objekt, jako je například vnořené [rozšíření značek StaticResource](staticresource-markup-extension.md).  
  
- <xref:System.Windows.Data.Binding.IsAsync%2A>: Logická hodnota, může být `true` buď `false`nebo. Výchozí hodnota je `false`.  
  
- <xref:System.Windows.Data.Binding.Mode%2A>: *Value* je název konstanty ze <xref:System.Windows.Data.BindingMode> výčtu. Například, `{Binding Mode=OneWay}`.  
  
- <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A>: Logická hodnota, může být `true` buď `false`nebo. Výchozí hodnota je `false`.  
  
- <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A>: Logická hodnota, může být `true` buď `false`nebo. Výchozí hodnota je `false`.  
  
- <xref:System.Windows.Data.Binding.NotifyOnValidationError%2A>: Logická hodnota, může být `true` buď `false`nebo. Výchozí hodnota je `false`.  
  
- <xref:System.Windows.Data.Binding.Path%2A>: řetězec, který popisuje cestu k datovému objektu nebo obecnému objektovému modelu. Formát poskytuje několik různých konvencí pro procházení objektového modelu, který nemůže být dostatečně popsán v tomto tématu. Viz [syntaxe jazyka XAML pro PropertyPath](propertypath-xaml-syntax.md).  
  
- <xref:System.Windows.Data.Binding.RelativeSource%2A>: vzájemně se <xref:System.Windows.Data.Binding.ElementName%2A> vylučují oproti <xref:System.Windows.Data.Binding.Source%2A>a; každá z těchto vlastností vazby představuje konkrétní metodologii vazby. Viz [Přehled datové vazby](../data/data-binding-overview.md). K určení hodnoty je vyžadováno vnořené použití [RelativeSource MarkupExtension](relativesource-markupextension.md) .  
  
- <xref:System.Windows.Data.Binding.Source%2A>: vzájemně se <xref:System.Windows.Data.Binding.RelativeSource%2A> vylučují <xref:System.Windows.Data.Binding.ElementName%2A>oproti a; každá z těchto vlastností vazby představuje konkrétní metodologii vazby. Viz [Přehled datové vazby](../data/data-binding-overview.md). Vyžaduje vnořené použití rozšíření, obvykle [rozšíření značek StaticResource](staticresource-markup-extension.md) , které odkazuje na zdroj dat objektu ze slovníku prostředků s klíčem.  
  
- <xref:System.Windows.Data.BindingBase.StringFormat%2A>: řetězec, který popisuje konvenci formátu řetězce pro vázaná data. Toto je poměrně pokročilý koncept vazby; viz Referenční stránka pro <xref:System.Windows.Data.BindingBase.StringFormat%2A>.  
  
- <xref:System.Windows.Data.BindingBase.TargetNullValue%2A>: lze nastavit jako `bindProp` = `value` řetězec ve výrazu, ale je závislý na typu předávaného parametru. Při předání typu odkazu pro hodnotu vyžaduje odkaz na objekt, jako je například vnořené [rozšíření značek StaticResource](staticresource-markup-extension.md).  
  
- <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>: *Value* je název konstanty ze <xref:System.Windows.Data.UpdateSourceTrigger> výčtu. Například, `{Binding UpdateSourceTrigger=LostFocus}`. Konkrétní ovládací prvky mohou mít různé výchozí hodnoty pro tuto vlastnost vazby. Viz <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.  
  
- <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A>: Logická hodnota, může být `true` buď `false`nebo. Výchozí hodnota je `false`. Viz poznámky.  
  
- <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A>: Logická hodnota, může být `true` buď `false`nebo. Výchozí hodnota je `false`. Viz poznámky.  
  
- <xref:System.Windows.Data.Binding.XPath%2A>: řetězec, který popisuje cestu k XMLDOM zdroje dat XML. Viz [vazba na data XML pomocí dotazů XmlDataProvider a XPath](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).  
  
 Níže jsou vlastnosti <xref:System.Windows.Data.Binding> , které nelze nastavit `Binding` pomocí formuláře s příponou označení/`{Binding}` výrazu.  
  
- <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>: Tato vlastnost očekává odkaz na implementaci zpětného volání. Zpětná volání/metody jiné než obslužné rutiny události nelze odkazovat v syntaxi jazyka XAML.  
  
- <xref:System.Windows.Data.Binding.ValidationRules%2A>: vlastnost přebírá obecnou kolekci <xref:System.Windows.Controls.ValidationRule> objektů. To může být vyjádřeno jako prvek vlastnosti v <xref:System.Windows.Data.Binding> prvku objektu, ale nemá žádnou snadno dostupnou techniku analýzy atributů pro použití `Binding` ve výrazu. Viz referenční téma pro <xref:System.Windows.Data.Binding.ValidationRules%2A>.  
  
- <xref:System.Windows.Data.Binding.XmlNamespaceManager%2A>  
  
## <a name="remarks"></a>Poznámky  
  
> [!IMPORTANT]
> V souladu s prioritou `Binding` vlastnosti závislosti je výraz ekvivalentem hodnoty v místní sadě. Pokud nastavíte místní hodnotu pro vlastnost, která dříve obsahovala `Binding` výraz `Binding` , je zcela odebrán. Podrobnosti najdete v tématu [Priorita hodnoty vlastností závislosti](dependency-property-value-precedence.md).  
  
 Popis datových vazeb na základní úrovni není popsaný v tomto tématu. Viz [Přehled datové vazby](../data/data-binding-overview.md).  
  
> [!NOTE]
> <xref:System.Windows.Data.MultiBinding><xref:System.Windows.Data.PriorityBinding> a[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] nepodporují syntaxi rozšíření. Místo toho byste měli použít prvky vlastností. Viz referenční témata pro <xref:System.Windows.Data.MultiBinding> a <xref:System.Windows.Data.PriorityBinding>.  
  
 Logické hodnoty pro XAML nerozlišují velká a malá písmena. Můžete například zadat buď `{Binding NotifyOnValidationError=true}` nebo. `{Binding NotifyOnValidationError=True}`  
  
 Vazby, které zahrnují ověření dat, jsou obvykle určeny explicitním `Binding` elementem a nikoli `{Binding ...}` jako výraz a nastavení <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> nebo <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> ve výrazu je Neběžné. Je to proto, že vlastnost <xref:System.Windows.Data.Binding.ValidationRules%2A> doprovodného výrazu nemůže být ve formuláři Expression snadno nastavena. Další informace naleznete v tématu [implementace ověřování vazby](../data/how-to-implement-binding-validation.md).  
  
 `Binding`je rozšíření značek. Rozšíření značek jsou obvykle implementována v případě, že je zapotřebí, aby hodnoty řídicích atributů byly jiné než hodnoty literálu nebo názvy obslužných rutin a požadavek je obecnější než konvertory typů s některými typy nebo vlastnostmi. Všechna rozšíření značek v jazyce XAML používají `{` ve `}` svých syntaxech atributů znaky a, což je konvence, pomocí níž procesor XAML rozpozná, že je nutné zpracovat obsah řetězce. Další informace naleznete v tématu [rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
 `Binding`je netypickým rozšířením značek v <xref:System.Windows.Data.Binding> tom, že třída, která implementuje funkce rozšíření pro implementaci XAML WPF, také implementuje několik dalších metod a vlastností, které nesouvisí s XAML. Ostatní členové jsou určeni pro <xref:System.Windows.Data.Binding> všestrannější a samostatnou třídu, která může řešit mnoho scénářů datové vazby kromě fungování jako rozšíření značek XAML.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Data.Binding>
- [Přehled datových vazeb](../data/data-binding-overview.md)
- [Přehled XAML (WPF)](xaml-overview-wpf.md)
- [Rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md)
