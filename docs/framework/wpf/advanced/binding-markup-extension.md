---
title: Rozšíření značek připojení
ms.date: 03/30/2017
f1_keywords:
- Binding
helpviewer_keywords:
- Binding markup extensions [WPF]
- XAML [WPF], Binding markup extension
ms.assetid: 83d6e2a4-1b0c-4fc8-bd96-b5e98800ab63
ms.openlocfilehash: d0a437e756da16db978d8074c4355fd83d211b67
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73453612"
---
# <a name="binding-markup-extension"></a>Rozšíření značek připojení
Odloží hodnotu vlastnosti na hodnotu vázanou na data, vytvoří objekt mezilehlého výrazu a interpretuje datový kontext, který se vztahuje na element a jeho vazbu v době běhu.  
  
## <a name="binding-expression-usage"></a>Použití výrazů vazby  
  
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
 V těchto syntaxech nejsou `[]` a `*` literály. Jsou součástí zápisu, který označuje, že je možné použít nula nebo více párů *bindProp*`=`*hodnot* s oddělovačem `,` a předchozími páry *bindProp*`=`*hodnoty* .  
  
 U všech vlastností uvedených v části "vlastnosti vazby, které lze nastavit pomocí rozšíření vazby" může být místo toho nastaveno pomocí atributů <xref:System.Windows.Data.Binding>ho prvku objektu. To však není ve skutečnosti použití rozšíření značek <xref:System.Windows.Data.Binding>, jedná se pouze o obecné zpracování XAML atributů, které nastavují vlastnosti třídy CLR <xref:System.Windows.Data.Binding>. Jinými slovy `<Binding` *bindProp1*`="`*hodnota1*`"[` *bindPropN*`="`*valueN*`"]*/>` je ekvivalentní Syntax pro atributy <xref:System.Windows.Data.Binding> použití prvků objektu místo použití výrazu `Binding`. Další informace o použití atributů XAML specifických vlastností <xref:System.Windows.Data.Binding>naleznete v části "použití atributu XAML" v příslušné vlastnosti <xref:System.Windows.Data.Binding> v knihovně tříd .NET Framework.  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|`bindProp1, bindPropN`|Název vlastnosti <xref:System.Windows.Data.Binding> nebo <xref:System.Windows.Data.BindingBase>, která se má nastavit. Nelze nastavit všechny vlastnosti <xref:System.Windows.Data.Binding> s rozšířením `Binding` a některé vlastnosti lze nastavit v rámci `Binding` výrazu pouze pomocí dalších vnořených rozšíření značek. Viz část "vlastnosti vazby, které lze nastavit pomocí rozšíření vazby".|  
|`value1, valueN`|Hodnota, na kterou má být vlastnost nastavena. Manipulace s hodnotou atributu je nakonec specifická pro typ a logiku konkrétní nastavované vlastnosti <xref:System.Windows.Data.Binding>.|  
|`path`|Řetězec cesty, který nastavuje vlastnost implicitního <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>. Viz také [PROPERTYPATH XAML Syntax](propertypath-xaml-syntax.md).|  
  
## <a name="unqualified-binding"></a>Nekvalifikované {Binding}  
 Použití `{Binding}`, které je uvedené v části "použití výrazů vazby", vytvoří objekt <xref:System.Windows.Data.Binding> s výchozími hodnotami, které zahrnují počáteční <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> `null`. To je stále užitečné v mnoha scénářích, protože vytvořené <xref:System.Windows.Data.Binding> se může spoléhat na vlastnosti vazby dat klíčů, jako je <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> a <xref:System.Windows.Data.Binding.Source%2A?displayProperty=nameWithType> nastavené v kontextu dat za běhu. Další informace o konceptu kontextu dat najdete v tématu [datové vazby](../data/data-binding-wpf.md).  
  
## <a name="implicit-path"></a>Implicitní cesta  
 Rozšíření `Binding` označení používá <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> jako koncepční "výchozí vlastnost", kde `Path=` nemusí být ve výrazu. Pokud zadáte výraz `Binding` s implicitní cestou, implicitní cesta musí být nejprve ve výrazu, před jakýmkoli jiným `bindProp`=`value` páry, kde je vlastnost <xref:System.Windows.Data.Binding> určena parametrem Name. Například: `{Binding PathString}`, kde `PathString` je řetězec, který je vyhodnocen jako hodnota <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> v <xref:System.Windows.Data.Binding> vytvořeném použitím rozšíření značek. Můžete připojit implicitní cestu k ostatním pojmenovaným vlastnostem za oddělovačem čárky, například `{Binding LastName, Mode=TwoWay}`.  
  
## <a name="binding-properties-that-can-be-set-with-the-binding-extension"></a>Vlastnosti vazby, které lze nastavit pomocí rozšíření vazby  
 Syntaxe zobrazená v tomto tématu používá obecné `bindProp`=`value` aproximaci, protože existuje mnoho vlastností pro čtení a zápis <xref:System.Windows.Data.BindingBase> nebo <xref:System.Windows.Data.Binding>, které lze nastavit prostřednictvím syntaxe `Binding` označení/výrazu. Lze je nastavit v libovolném pořadí, s výjimkou implicitního <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>. (K dispozici máte možnost explicitně zadat `Path=`, v takovém případě ji můžete nastavit v libovolném pořadí). V podstatě můžete nastavit nula nebo více vlastností v seznamu níže pomocí `bindProp`=`value` páry oddělené čárkami.  
  
 Některé z těchto hodnot vlastností vyžadují typy objektů, které nepodporují převod nativního typu z syntaxe textu v jazyce XAML, a proto vyžadují rozšíření značek, aby je bylo možné nastavit jako hodnotu atributu. Další informace najdete v části použití atributů XAML v knihovně tříd .NET Framework pro každou vlastnost. řetězec, který použijete pro syntaxi atributu XAML s nebo bez dalšího použití rozšíření značek, je v podstatě stejný jako hodnota, kterou zadáte ve výrazu `Binding`, s výjimkou, že se u každého `bindProp`=`value` neumísťují uvozovky. výraz `Binding`.  
  
- <xref:System.Windows.Data.BindingBase.BindingGroupName%2A>: řetězec, který identifikuje možnou skupinu vazeb. Toto je poměrně pokročilý koncept vazby; <xref:System.Windows.Data.BindingBase.BindingGroupName%2A>najdete na referenční stránce.  
  
- <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A>: Boolean, může být buď `true` nebo `false`. Výchozí hodnota je `false`.  
  
- <xref:System.Windows.Data.Binding.Converter%2A>: lze nastavit jako `bindProp`=`value` řetězec ve výrazu, ale k tomu je zapotřebí odkaz na objekt pro hodnotu, jako je například [rozšíření značek StaticResource](staticresource-markup-extension.md). Hodnota v tomto případě je instancí vlastní třídy převaděče.  
  
- <xref:System.Windows.Data.Binding.ConverterCulture%2A>: ve výrazu nastavit jako identifikátor založený na standardech; <xref:System.Windows.Data.Binding.ConverterCulture%2A>najdete v referenčním tématu.  
  
- <xref:System.Windows.Data.Binding.ConverterParameter%2A>: lze nastavit jako `bindProp`=`value` řetězec ve výrazu, ale to závisí na typu předávaného parametru. Při předání typu odkazu pro hodnotu toto použití vyžaduje odkaz na objekt, jako je například vnořená [přípona značek StaticResource](staticresource-markup-extension.md).  
  
- <xref:System.Windows.Data.Binding.ElementName%2A>: vzájemně se vylučují a <xref:System.Windows.Data.Binding.RelativeSource%2A> a <xref:System.Windows.Data.Binding.Source%2A>; Každá z těchto vlastností vazby představuje konkrétní metodologii vazby. Viz [Přehled datové vazby](../data/data-binding-overview.md).  
  
- <xref:System.Windows.Data.BindingBase.FallbackValue%2A>: lze nastavit jako `bindProp`=`value` řetězec ve výrazu, ale to závisí na typu předávané hodnoty. Při předání typu odkazu vyžaduje odkaz na objekt, jako je například vnořené [rozšíření značek StaticResource](staticresource-markup-extension.md).  
  
- <xref:System.Windows.Data.Binding.IsAsync%2A>: Boolean, může být buď `true` nebo `false`. Výchozí hodnota je `false`.  
  
- <xref:System.Windows.Data.Binding.Mode%2A>: *hodnota* je konstantní název z výčtu <xref:System.Windows.Data.BindingMode>. Například `{Binding Mode=OneWay}`.  
  
- <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A>: Boolean, může být buď `true` nebo `false`. Výchozí hodnota je `false`.  
  
- <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A>: Boolean, může být buď `true` nebo `false`. Výchozí hodnota je `false`.  
  
- <xref:System.Windows.Data.Binding.NotifyOnValidationError%2A>: Boolean, může být buď `true` nebo `false`. Výchozí hodnota je `false`.  
  
- <xref:System.Windows.Data.Binding.Path%2A>: řetězec, který popisuje cestu k datovému objektu nebo obecnému objektovému modelu. Formát poskytuje několik různých konvencí pro procházení objektového modelu, který nemůže být dostatečně popsán v tomto tématu. Viz [syntaxe jazyka XAML pro PropertyPath](propertypath-xaml-syntax.md).  
  
- <xref:System.Windows.Data.Binding.RelativeSource%2A>: vzájemně se vylučují proti <xref:System.Windows.Data.Binding.ElementName%2A> a <xref:System.Windows.Data.Binding.Source%2A>; Každá z těchto vlastností vazby představuje konkrétní metodologii vazby. Viz [Přehled datové vazby](../data/data-binding-overview.md). K určení hodnoty je vyžadováno vnořené použití [RelativeSource MarkupExtension](relativesource-markupextension.md) .  
  
- <xref:System.Windows.Data.Binding.Source%2A>: vzájemně se vylučují a <xref:System.Windows.Data.Binding.RelativeSource%2A> a <xref:System.Windows.Data.Binding.ElementName%2A>; Každá z těchto vlastností vazby představuje konkrétní metodologii vazby. Viz [Přehled datové vazby](../data/data-binding-overview.md). Vyžaduje vnořené použití rozšíření, obvykle [rozšíření značek StaticResource](staticresource-markup-extension.md) , které odkazuje na zdroj dat objektu ze slovníku prostředků s klíčem.  
  
- <xref:System.Windows.Data.BindingBase.StringFormat%2A>: řetězec, který popisuje konvenci formátu řetězce pro vázaná data. Toto je poměrně pokročilý koncept vazby; <xref:System.Windows.Data.BindingBase.StringFormat%2A>najdete na referenční stránce.  
  
- <xref:System.Windows.Data.BindingBase.TargetNullValue%2A>: lze nastavit jako `bindProp`=`value` řetězec ve výrazu, ale to závisí na typu předávaného parametru. Při předání typu odkazu pro hodnotu vyžaduje odkaz na objekt, jako je například vnořené [rozšíření značek StaticResource](staticresource-markup-extension.md).  
  
- <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>: *hodnota* je konstantní název z výčtu <xref:System.Windows.Data.UpdateSourceTrigger>. Například `{Binding UpdateSourceTrigger=LostFocus}`. Konkrétní ovládací prvky mohou mít různé výchozí hodnoty pro tuto vlastnost vazby. Viz <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.  
  
- <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A>: Boolean, může být buď `true` nebo `false`. Výchozí hodnota je `false`. Viz poznámky.  
  
- <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A>: Boolean, může být buď `true` nebo `false`. Výchozí hodnota je `false`. Viz poznámky.  
  
- <xref:System.Windows.Data.Binding.XPath%2A>: řetězec, který popisuje cestu k XMLDOM zdroje dat XML. Viz [vazba na data XML pomocí dotazů XmlDataProvider a XPath](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).  
  
 Níže jsou uvedeny vlastnosti <xref:System.Windows.Data.Binding>, které nelze nastavit pomocí `Binding`ho rozšíření značek/`{Binding}` formuláře výrazu.  
  
- <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>: Tato vlastnost očekává odkaz na implementaci zpětného volání. Zpětná volání/metody jiné než obslužné rutiny události nelze odkazovat v syntaxi jazyka XAML.  
  
- <xref:System.Windows.Data.Binding.ValidationRules%2A>: vlastnost přebírá obecnou kolekci objektů <xref:System.Windows.Controls.ValidationRule>. To může být vyjádřeno jako prvek vlastnosti v prvku <xref:System.Windows.Data.Binding> objektu, ale nemá k dispozici žádnou snadno dostupnou techniku analýzy atributů pro použití ve výrazu `Binding`. <xref:System.Windows.Data.Binding.ValidationRules%2A>najdete v referenčním tématu.  
  
- <xref:System.Windows.Data.Binding.XmlNamespaceManager%2A>  
  
## <a name="remarks"></a>Poznámky  
  
> [!IMPORTANT]
> V souladu s prioritou vlastnosti závislosti je výraz `Binding` ekvivalentem hodnoty v místním nastavení. Pokud nastavíte místní hodnotu pro vlastnost, která dříve obsahovala výraz `Binding`, `Binding` je zcela odebrán. Podrobnosti najdete v tématu [Priorita hodnoty vlastností závislosti](dependency-property-value-precedence.md).  
  
 Popis datových vazeb na základní úrovni není popsaný v tomto tématu. Viz [Přehled datové vazby](../data/data-binding-overview.md).  
  
> [!NOTE]
> <xref:System.Windows.Data.MultiBinding> a <xref:System.Windows.Data.PriorityBinding> nepodporují syntaxi rozšíření [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Místo toho byste měli použít prvky vlastností. <xref:System.Windows.Data.MultiBinding> a <xref:System.Windows.Data.PriorityBinding>najdete v referenčních tématech.  
  
 Logické hodnoty pro XAML nerozlišují velká a malá písmena. Můžete například zadat buď `{Binding NotifyOnValidationError=true}`, nebo `{Binding NotifyOnValidationError=True}`.  
  
 Vazby, které zahrnují ověření dat, jsou obvykle určeny explicitním `Binding` prvkem, nikoli jako výraz `{Binding ...}` a nastavení <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> nebo <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> ve výrazu je Neběžné. Je to proto, že vlastnost doprovodného <xref:System.Windows.Data.Binding.ValidationRules%2A> nemůže být ve formuláři Expression snadno nastavena. Další informace naleznete v tématu [implementace ověřování vazby](../data/how-to-implement-binding-validation.md).  
  
 `Binding` je rozšíření značek. Rozšíření značek jsou obvykle implementována v případě, že je zapotřebí, aby hodnoty řídicích atributů byly jiné než hodnoty literálu nebo názvy obslužných rutin a požadavek je obecnější než konvertory typů s některými typy nebo vlastnostmi. Všechna rozšíření značek v jazyce XAML používají ve své syntaxi atributu `{` a `}` znaky, což je konvence, podle které procesor XAML rozpozná, že je nutné zpracovat obsah řetězce pomocí rozšíření značek. Další informace naleznete v tématu [rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md).  
  
 `Binding` je neobvyklá přípona značek v tom, že <xref:System.Windows.Data.Binding> třída, která implementuje funkce rozšíření pro implementaci XAML WPF, také implementuje několik dalších metod a vlastností, které se nevztahují k XAML. Ostatní členové mají <xref:System.Windows.Data.Binding>ější a samostatnou třídu, která může řešit mnoho scénářů datové vazby kromě fungování jako rozšíření značek XAML.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Data.Binding>
- [Přehled datových vazeb](../data/data-binding-overview.md)
- [Přehled XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Rozšíření značek a WPF XAML](markup-extensions-and-wpf-xaml.md)
