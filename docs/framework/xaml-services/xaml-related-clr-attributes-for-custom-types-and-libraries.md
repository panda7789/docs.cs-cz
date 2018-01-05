---
title: "Atributy CLR související s jazykem XAML pro vlastní typy a knihovny"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: CLR attributes for custom types [XAML Services]
ms.assetid: 5dfb299a-b6e2-41b8-8694-e6ac987547f1
caps.latest.revision: "8"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 25aac1d4478279561cbcdda6c1cf912c3c3b2cde
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="xaml-related-clr-attributes-for-custom-types-and-libraries"></a>Atributy CLR související s jazykem XAML pro vlastní typy a knihovny
Toto téma popisuje běžné atributy modulu runtime (CLR) jazyk, které jsou definované rozhraní .NET Framework XAML Services. Popisuje také jiné CLR atributy, které jsou definovány v rozhraní .NET Framework s scénáři související s jazykem XAML pro aplikaci na sestavení nebo typy. Zapisujících sestavení, typy a členy s těmito atributy CLR poskytuje XAML typ systémové informace související s vaší typy. Informace jsou poskytovány na všechny XAML příjemce, který používá rozhraní .NET Framework XAML Services pro zpracování datový proud uzlu XAML přímo nebo prostřednictvím vyhrazené čteček XAML a XAML zapisovače.  
  
## <a name="xaml-related-clr-attributes-for-custom-types-and-custom-members"></a>Atributy CLR související s jazykem XAML pro vlastní typy a vlastní členy  
 Pomocí atributů CLR má za následek, že používáte celkové CLR definovat vaše typy, jinak takové atributy nejsou k dispozici. Pokud používáte k definování zálohování typu modulu CLR, může číst výchozí kontext schématu XAML používá rozhraní .NET Framework XAML Services XAML zapisovače CLR uvedení prostřednictvím reflexe proti zálohování sestavení.  
  
 Následující části popisují související s jazykem XAML atributy, které můžete použít pro vlastní typy nebo vlastní členy. Každý atribut CLR komunikuje informace, které jsou relevantní pro systém typů XAML. V cestě zatížení s atributy informace buď pomáhá čtečce XAML formuláři platný datový proud uzlu XAML nebo pomáhá XAML zapisovač vytvořit platný objekt grafu. V poli Uložit cestu, s atributy informace buď pomáhá čtečce XAML formuláři platný datový proud uzlu XAML, který reconstitutes informace o systému typ XAML; nebo deklaruje požadavky pro ostatní příjemce XAML nebo zapisovač XAML nebo pomocné parametry serializace.  
  
### <a name="ambientattribute"></a>AmbientAttribute  
 **Referenční dokumentace:**  <xref:System.Windows.Markup.AmbientAttribute>  
  
 **Platí pro:** třídy, vlastnosti, nebo `get` přistupujícího objektu členy, které podporují připojitelné vlastnosti.  
  
 **Argumenty:** None  
  
 <xref:System.Windows.Markup.AmbientAttribute>Označuje, vlastnost nebo všechny vlastnosti, které s atributy typu by měl být interpretován pod – vedlejší vlastnost koncept v jazyce XAML. Vedlejším koncept se vztahuje k jak XAML procesory určí typ vlastníky členů. Vedlejší vlastnost je vlastností, kde hodnota musí být dostupné v kontextu analyzátor při vytváření grafu objektu, ale kde vyhledávání typický typ člena je pozastavená okamžitou uzlu XAML nastavit vytváří.  
  
 Vedlejším koncept lze použít pro připojitelné členy, které nejsou reprezentovány jako vlastnosti z hlediska jak definuje CLR uvedení <xref:System.AttributeTargets>. Využití uvedení metoda má být použita pouze u `get` přistupujícího objektu, který podporuje připojitelné využití pro jazyk XAML.  
  
### <a name="constructorargumentattribute"></a>ConstructorArgumentAttribute  
 **Referenční dokumentace:**  <xref:System.Windows.Markup.ConstructorArgumentAttribute>  
  
 **Platí pro:** – třída  
  
 **Argumenty:** řetězec, který určuje název vlastnosti, která odpovídá konstruktor jeden argument.  
  
 <xref:System.Windows.Markup.ConstructorArgumentAttribute>Určuje, že jde inicializovat objekt pomocí jiné než výchozí konstruktor Syntaxe a že vlastnost se zadaným názvem poskytuje informace o vytváření. Tyto informace jsou především pro serializaci XAML. Další informace naleznete v tématu <xref:System.Windows.Markup.ConstructorArgumentAttribute>.  
  
### <a name="contentpropertyattribute"></a>ContentPropertyAttribute  
 **Referenční dokumentace:**  <xref:System.Windows.Markup.ContentPropertyAttribute>  
  
 **Platí pro:** – třída  
  
 **Argumenty:** řetězec, který určuje název člena s atributy typu.  
  
 <xref:System.Windows.Markup.ContentPropertyAttribute>Označuje, že vlastnost jako s názvem argumentem by měla sloužit jako vlastnost XAML pro tento typ obsahu. Vlastnost obsahu definici XAML dědí pro všechny odvozené typy, které jsou přiřadit k definování typu. Definice pro konkrétní odvozený typ můžete přepsat použitím <xref:System.Windows.Markup.ContentPropertyAttribute> na konkrétním odvozeného typu.  
  
 Pro vlastnost, která slouží jako vlastnost obsahu XAML můžete vynechat element vlastnosti označování pro vlastnost využití XAML. Obvykle je určit XAML obsahu vlastnosti, které podporují zjednodušenou kód XAML pro modely obsah a členství ve skupině. Vzhledem k tomu, že lze určit pouze jeden člen jako vlastnost obsahu XAML, máte někdy volbám návrhu aby, díky kterým několik kontejneru vlastnosti typu by měla být určena jako vlastnost obsahu XAML. Ostatní vlastnosti kontejneru musí použít u elementů na explicitní vlastnost.  
  
 V datový proud uzlu XAML obsahu vlastností XAML stále vytvořit `StartMember` a `EndMember` uzly, název vlastnosti pro použití <xref:System.Xaml.XamlMember>. Pokud chcete zjistit, zda je člen vlastnost obsahu XAML, zkontrolujte <xref:System.Xaml.XamlType> z hodnoty `StartObject` pozice a získávání hodnoty <xref:System.Xaml.XamlType.ContentProperty%2A>.  
  
### <a name="contentwrapperattribute"></a>ContentWrapperAttribute  
 **Referenční dokumentace:**  <xref:System.Windows.Markup.ContentWrapperAttribute>  
  
 **Platí pro:** třída, konkrétně typy kolekcí.  
  
 **Argumenty:** A <xref:System.Type> určující typ, který má používat jako typ obsahu obálku cizí obsahu.  
  
 <xref:System.Windows.Markup.ContentWrapperAttribute>Určuje jeden nebo více typů na typ přidružený kolekce, který slouží k zabalení cizí obsah. Cizí obsah odkazuje na případy omezení systému typu pro typ obsahu vlastnosti kde není zachytíte všechny možné obsahu případů, které by podporovat použití XAML pro typ vlastnícím. Například podporovat XAML pro konkrétní typ obsahu může podporovat řetězce v silného typu Obecné <xref:System.Collections.ObjectModel.Collection%601>. Obsahu obálky jsou užitečné pro migraci dříve existující konvence značek do XAML pro koncepci Přiřaditelné hodnoty pro kolekce, jako je například migrace související s textem obsahu modelů.  
  
 Chcete-li zadat více než jeden typ obsahu obálky, použíjte atribut vícekrát.  
  
### <a name="dependsonattribute"></a>DependsOnAttribute  
 **Referenční dokumentace:**  <xref:System.Windows.Markup.DependsOnAttribute>  
  
 **Platí pro:** vlastnost  
  
 **Argumenty:** řetězec, který určuje název jiného člena s atributy typu.  
  
 <xref:System.Windows.Markup.DependsOnAttribute>Označuje, že vlastnost s atributy závisí na hodnotu jiné vlastnosti. Použití tohoto atributu na definici vlastnosti zajistí, že závislé vlastnosti jsou zpracován jako první při psaní objekt XAML. Použití <xref:System.Windows.Markup.DependsOnAttribute> zadejte výjimečných případech vlastností na typy, kde je potřeba dodržovat konkrétní pořadí analýzy pro vytvoření platný objekt.  
  
 Můžete použít více <xref:System.Windows.Markup.DependsOnAttribute> případů definici vlastnosti.  
  
### <a name="markupextensionreturntypeattribute"></a>MarkupExtensionReturnTypeAttribute  
 **Referenční dokumentace:**  <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute>  
  
 **Platí pro:** třídy, která se očekává <xref:System.Windows.Markup.MarkupExtension> odvozeného typu.  
  
 **Argumenty:** A <xref:System.Type> určující typ nejpřesnější mohou očekávat, jako `ProvideValue` výsledek s atributy <xref:System.Windows.Markup.MarkupExtension>.  
  
 Další informace najdete v tématu [XAML přehled rozšíření značek pro](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md).  
  
### <a name="namescopepropertyattribute"></a>NameScopePropertyAttribute  
 **Referenční dokumentace:**  <xref:System.Windows.Markup.NameScopePropertyAttribute>  
  
 **Platí pro:** – třída  
  
 **Argumenty:** podporuje dvě formy uvedení:  
  
-   Řetězec, který určuje název vlastnosti na typ s atributy.  
  
-   Řetězec, který určuje název vlastnosti a <xref:System.Type> pro typ, který definuje vlastnost s názvem. Tento formulář slouží k určení člena připojitelné jako vlastnost namescope XAML.  
  
 <xref:System.Windows.Markup.NameScopePropertyAttribute>Určuje vlastnosti, která obsahuje hodnotu namescope XAML pro třídu s atributy. Vlastnost namescope XAML musí odkazovat na objekt, který implementuje <xref:System.Windows.Markup.INameScope> a obsahuje skutečné namescope XAML, jeho úložiště a jeho chování.  
  
### <a name="runtimenamepropertyattribute"></a>RuntimeNamePropertyAttribute  
 **Referenční dokumentace:**  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>  
  
 **Platí pro:** – třída  
  
 **Argumenty:** řetězec, který určuje název vlastnosti názvu běhu na typ s atributy.  
  
 <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>sestavy vlastnost s atributy typu, který se mapuje na XAML [x: Name – direktiva](../../../docs/framework/xaml-services/x-name-directive.md). Vlastnost musí být typu <xref:System.String> a musí být pro čtení a zápis.  
  
 Definice dědí pro všechny odvozené typy, které jsou přiřadit k definování typu. Definice pro konkrétní odvozený typ můžete přepsat použitím <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> na konkrétním odvozeného typu.  
  
### <a name="trimsurroundingwhitespaceattribute"></a>TrimSurroundingWhitespaceAttribute  
 **Referenční dokumentace:**  <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>  
  
 **Platí pro:** typy  
  
 **Argumenty:** None.  
  
 <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>platí pro konkrétní typy, které se mohou zobrazit jako podřízených elementů v rámci významné obsah prázdné znaky (obsah držené kolekce, která má <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>). <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>je důležité především pro uložení cesta, ale je k dispozici v systému typu XAML v cestě zatížení tak, že prověří <xref:System.Xaml.XamlType.TrimSurroundingWhitespace%2A?displayProperty=nameWithType>. Další informace najdete v tématu [zpracování prázdných znaků v jazyce XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).  
  
### <a name="typeconverterattribute"></a>TypeConverterAttribute  
 **Referenční dokumentace:**  <xref:System.ComponentModel.TypeConverterAttribute>  
  
 **Platí pro:** třídy, vlastností, metoda (jediný XAML platná metoda případem je `get` přistupujícího objektu, který podporuje připojitelné člen).  
  
 **Argumenty:** <xref:System.Type> z <xref:System.ComponentModel.TypeConverter>.  
  
 <xref:System.ComponentModel.TypeConverterAttribute>v XAML kontext odkazuje na vlastní <xref:System.ComponentModel.TypeConverter>. To <xref:System.ComponentModel.TypeConverter> poskytuje typ převodu chování pro vlastní typy nebo členy tohoto typu.  
  
 Můžete použít <xref:System.ComponentModel.TypeConverterAttribute> atribut typu vašeho odkazující na implementaci typ převaděče. Můžete definovat převaděčů typů pro jazyk XAML na třídy, struktury nebo rozhraní. Není nutné poskytnout převod typů pro výčty, nativně povolen převod.  
  
 Převést z řetězce, který se používá pro atributy nebo inicializace text v kódu, do zamýšlené cílový typ. byste měli mít vaše převaděče typů. Další informace najdete v tématu [TypeConverters a XAML](../../../docs/framework/wpf/advanced/typeconverters-and-xaml.md).  
  
 Místo použití pro všechny hodnoty typu, můžete o chování typu převaděč pro jazyk XAML také navázat na určité vlastnosti. V takovém případě použijete <xref:System.ComponentModel.TypeConverterAttribute> k definici vlastnosti (vnější definice, nikoli konkrétní `get` a `set` definice).  
  
 Chování typu převaděč pro použití XAML vlastní připojitelné člena lze přiřadit použitím <xref:System.ComponentModel.TypeConverterAttribute> k `get` přistupujícího objektu metoda, která podporuje použití XAML.  
  
 Podobně jako <xref:System.ComponentModel.TypeConverter>, <xref:System.ComponentModel.TypeConverterAttribute> existovalo v rozhraní .NET Framework před existenci XAML a typ modelu převaděč poskytovaného jiné účely. Chcete-li odkazovat a využívat <xref:System.ComponentModel.TypeConverterAttribute>, musí plně kvalifikaci ho nebo zadejte `using` příkaz pro <xref:System.ComponentModel>. Sestavení systému musí obsahovat také ve vašem projektu.  
  
### <a name="uidpropertyattribute"></a>UidPropertyAttribute  
 **Referenční dokumentace:**  <xref:System.Windows.Markup.UidPropertyAttribute>  
  
 **Platí pro:** – třída  
  
 **Argumenty:** řetězec, který odkazuje vlastnost relevantní podle názvu.  
  
 Vlastnost CLR třídy označuje, že aliasy [x: Uid – direktiva](../../../docs/framework/xaml-services/x-uid-directive.md).  
  
### <a name="usableduringinitializationattribute"></a>UsableDuringInitializationAttribute  
 **Referenční dokumentace:**  <xref:System.Windows.Markup.UsableDuringInitializationAttribute>  
  
 **Platí pro:** – třída  
  
 **Argumenty:** logickou hodnotu. Pokud chcete použít pro zamýšlený účel atributu, to by měl vždy třeba zadat jako `true`.  
  
 Určuje, zda tento typ je sestavena shora dolů během vytváření graf objektů jazyka XAML. Toto je pokročilé koncept, což je pravděpodobně úzce související definice programovací model. Další informace naleznete v tématu <xref:System.Windows.Markup.UsableDuringInitializationAttribute>.  
  
### <a name="valueserializerattribute"></a>ValueSerializerAttribute  
 **Referenční dokumentace:**  <xref:System.Windows.Markup.ValueSerializerAttribute>  
  
 **Platí pro:** třídy, vlastností, metoda (jediný XAML platná metoda případem je `get` přistupujícího objektu, který podporuje připojitelné člen).  
  
 **Argumenty:** A <xref:System.Type> vlastnost s konkrétní atributy nebo určuje třídu podporu serializátor hodnoty, které se má použít při serializaci všechny vlastnosti typu s atributy.  
  
 <xref:System.Windows.Markup.ValueSerializer>Určuje třídu serializace hodnotu, která vyžaduje další stav a kontextu než <xref:System.ComponentModel.TypeConverter> nepodporuje. <xref:System.Windows.Markup.ValueSerializer>může být přidružen připojitelné člena s použitím <xref:System.Windows.Markup.ValueSerializerAttribute> atribut u statických `get` přístupovou metodu pro připojitelné člena. Hodnota serializace platí i pro vytváření výčtů a rozhraní a struktury, ale ne pro delegáti.  
  
### <a name="whitespacesignificantcollectionattribute"></a>WhitespaceSignificantCollectionAttribute  
 **Referenční dokumentace:**  <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>  
  
 **Platí pro:** třída, konkrétně typy kolekcí, které budou hostovat smíšený obsah, kde mezer kolem elementy objektu může být důležité pro znázornění uživatelského rozhraní.  
  
 **Argumenty:** None.  
  
 <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>Označuje, že typ kolekce, měla by být zpracována jako prázdné významné procesorem XAML, který ovlivňuje konstrukce datový proud uzlu XAML hodnota uzlů v rámci kolekce. Další informace najdete v tématu [zpracování prázdných znaků v jazyce XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).  
  
### <a name="xamldeferloadattribute"></a>XamlDeferLoadAttribute  
 **Referenční dokumentace:**  <xref:System.Windows.Markup.XamlDeferLoadAttribute>  
  
 **Platí pro:** třídy, vlastnosti.  
  
 **Argumenty:** uvedení podporuje dva typy jako řetězce forms nebo typy jako <xref:System.Type>. V tématu <xref:System.Windows.Markup.XamlDeferLoadAttribute>.  
  
 Označuje, že třídu nebo vlastnost má použití odložené zatížení pro jazyk XAML (například šablony chování) a sestavy třídu, která umožňuje odložení chování a její typ cílové a obsah.  
  
### <a name="xamlsetmarkupextensionattribute"></a>XamlSetMarkupExtensionAttribute  
 **Referenční dokumentace:**  <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute>  
  
 **Platí pro:** – třída  
  
 **Argumenty:** názvy zpětné volání.  
  
 Označuje, že můžete použít rozšíření značek k zajištění hodnotu pro jeden nebo více vlastností třídy a odkazuje na obslužnou rutinu, která zapisovač XAML by měly volat před provedením operace set rozšíření značek na žádnou vlastnost třídy.  
  
### <a name="xamlsettypeconverterattribute"></a>XamlSetTypeConverterAttribute  
 **Referenční dokumentace:**  <xref:System.Windows.Markup.XamlSetTypeConverterAttribute>  
  
 **Platí pro:** – třída  
  
 **Argumenty:** názvy zpětné volání.  
  
 Označuje, že můžete převaděče typů zadat hodnotu pro jeden nebo více vlastností třídy a odkazuje na obslužnou rutinu, která zapisovač XAML by měly volat před provedením operace set převaděče typu na žádnou vlastnost třídy.  
  
### <a name="xmllangpropertyattribute"></a>XmlLangPropertyAttribute  
 **Referenční dokumentace:**  <xref:System.Windows.Markup.XmlLangPropertyAttribute>  
  
 **Platí pro:** – třída  
  
 **Argumenty:** řetězec, který určuje název vlastnosti, která má alias `xml:lang` na typ s atributy.  
  
 <xref:System.Windows.Markup.XmlLangPropertyAttribute>sestavy vlastnost s atributy typu, který se mapuje na XML `lang` – direktiva. Vlastnost není typu nutně <xref:System.String>, ale musí být přiřadit z řetězce (to je možné dosáhnout tím, že přidružíte převaděče typů typu vlastnosti, nebo s určitou vlastnost). Vlastnost, musí být pro čtení a zápis.  
  
 Tento scénář pro mapování `xml:lang` je tak, aby objektový model runtime má přístup k informacím jazyka XML zadaný bez konkrétně zpracování s XMLDOM.  
  
 Definice dědí pro všechny odvozené typy, které jsou přiřadit k definování typu. Definice pro konkrétní odvozený typ můžete přepsat použitím <xref:System.Windows.Markup.XmlLangPropertyAttribute> na konkrétním odvozený typ, který sice neobvyklé scénáře.  
  
## <a name="xaml-related-clr-attributes-at-the-assembly-level"></a>Atributy CLR související s jazykem XAML na úrovni sestavení  
 Následující části popisují související s jazykem XAML atributy, které nejsou u typů nebo člen definice, ale místo toho se použijí k sestavení. Tyto atributy jsou vztahujících se k obecným cílem definování knihovnu, která obsahuje vlastní typy, které se použijí v jazyce XAML. Některé atributy není nutně vliv datový proud uzlu XAML přímo, ale jsou předané datový proud uzlu pro jiné příjemcům používat. Příjemci informace zahrnují prostředí návrhu a serializace procesy, které potřebují informace oboru názvů jazyka XAML a přidružené informace předponu. XAML schématu kontextu (včetně výchozí rozhraní .NET Framework XAML Services) také používá tyto informace.  
  
### <a name="xmlnscompatiblewithattribute"></a>XmlnsCompatibleWithAttribute  
 **Referenční dokumentace:**  <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>  
  
 **Argumenty:**  
  
-   Řetězec, který určuje identifikátor oboru názvů jazyka XAML k začlenění.  
  
-   Řetězec, který určuje identifikátor oboru názvů jazyka XAML, který můžete začlenění oboru názvů jazyka XAML z předchozí argumentu.  
  
 <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>Určuje, že může být oboru názvů jazyka XAML subsumed pomocí jiného oboru názvů jazyka XAML. Obvykle je uvedené subsuming oboru názvů jazyka XAML v dříve definovaném <xref:System.Windows.Markup.XmlnsDefinitionAttribute>. Tento postup lze použít pro správu verzí XAML termínů v knihovně a aby byl kompatibilní s dříve definovaném značek u starších verzí termínů.  
  
### <a name="xmlnsdefinitionattribute"></a>XmlnsDefinitionAttribute  
 **Referenční dokumentace:**  <xref:System.Windows.Markup.XmlnsDefinitionAttribute>  
  
 **Argumenty:**  
  
-   Řetězec, který určuje identifikátor oboru názvů jazyka XAML definovat.  
  
-   Řetězec s názvem oboru názvů CLR. Obor názvů CLR měli definovat veřejné typy v sestavení a alespoň jeden z typů CLR obor názvů by měl být určené pro použití XAML.  
  
 <xref:System.Windows.Markup.XmlnsDefinitionAttribute>Určuje mapování na základě za sestavení mezi oboru názvů jazyka XAML a CLR názvů, který je pak použit pro vyřešení typu zapisovače objektu XAML nebo kontext schématu XAML.  
  
 Více než jeden <xref:System.Windows.Markup.XmlnsDefinitionAttribute> lze použít k sestavení. To může být provedeno pro libovolnou kombinaci z následujících důvodů:  
  
-   Návrh knihovna obsahuje více oborů názvů CLR pro logické organizace přístup pomocí rozhraní API běhu; však chcete, aby byla použitelná pro XAML odkazem stejného oboru názvů jazyka XAML všechny typy v obory názvů. V takovém případě můžete použít několik <xref:System.Windows.Markup.XmlnsDefinitionAttribute> atributy používající stejný <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> hodnota ale odlišným <xref:System.Windows.Markup.XmlnsDefinitionAttribute.ClrNamespace%2A> hodnoty. To je obzvláště užitečné, pokud jsou definice mapování oboru názvů jazyka XAML, kterou framework nebo aplikace chce být výchozí obor názvů jazyka XAML běžné využití.  
  
-   Návrh knihovna obsahuje více oborů názvů CLR a chcete, aby záměrné rozdělení oboru názvů jazyka XAML mezi použití typy v oborech názvů těchto CLR.  
  
-   Zadejte obor názvů CLR v sestavení a chcete, aby byly přístupné prostřednictvím více než jednoho oboru názvů jazyka XAML. K této situaci dojde, pokud podporujete více vocabularies s stejném základu kódu.  
  
-   Podpora jazyka XAML definujete v jedné nebo více oborů názvů CLR. Pro tyto <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> hodnota by měla být `http://schemas.microsoft.com/winfx/2006/xaml`.  
  
### <a name="xmlnsprefixattribute"></a>XmlnsPrefixAttribute  
 **Referenční dokumentace:**  <xref:System.Windows.Markup.XmlnsPrefixAttribute>  
  
 **Argumenty:**  
  
-   Řetězec, který určuje identifikátor oboru názvů jazyka XAML.  
  
-   Řetězec, který určuje předponu doporučené.  
  
 <xref:System.Windows.Markup.XmlnsDefinitionAttribute>Určuje doporučené předponu pro obor názvů jazyka XAML. Předpona, která je užitečné, když zápis elementů a atributů v souboru XAML, který je serializovat rozhraní .NET Framework XAML Services <xref:System.Xaml.XamlXmlWriter>, nebo když knihovnu implementace XAML komunikuje s prostředí návrhu, který má XAML úpravy funkce.  
  
 Více než jeden <xref:System.Windows.Markup.XmlnsPrefixAttribute> lze použít k sestavení. To může být provedeno pro libovolnou kombinaci z následujících důvodů:  
  
-   Vaše sestavení definuje typy pro více než jednoho oboru názvů jazyka XAML. V takovém případě byste měli definovat různých předpon pro každý obor názvů jazyka XAML.  
  
-   Jsou podporovány více vocabularies a používání různých předpon pro každou termínů a oboru názvů jazyka XAML.  
  
-   Můžete určit podporu jazyka XAML v sestavení a <xref:System.Windows.Markup.XmlnsDefinitionAttribute> pro `http://schemas.microsoft.com/winfx/2006/xaml`. V takovém případě je obvykle by měly podporovat předponu `x`.  
  
> [!NOTE]
>  Rozhraní .NET framework XAML Services také definuje atribut související s jazykem XAML <xref:System.Windows.Markup.RootNamespaceAttribute>. Tento atribut je atribut úrovně sestavení pro podporu systému projektu a není relevantní pro vlastní typy XAML.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Attribute>  
 [Definování vlastních typů pro práci s technologií .NET Framework XAML Services](../../../docs/framework/xaml-services/defining-custom-types-for-use-with-net-framework-xaml-services.md)
