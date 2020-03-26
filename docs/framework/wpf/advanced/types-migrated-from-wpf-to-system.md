---
title: Typy migrované z prostředí WPF do oboru názvů System.Xaml
ms.date: 03/30/2017
helpviewer_keywords:
- WPF XAML [XAML Services], migration to System.Xaml
- XAML [XAML Services], System.Xaml and WPF
- System.Xaml [XAML Services], types migrated from WPF
ms.assetid: d79dabf5-a2ec-4e8d-a37a-67c4ba8a2b91
ms.openlocfilehash: 5aa2d8a39be47d9affb97c3b60e53c4722c63cce
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249800"
---
# <a name="types-migrated-from-wpf-to-systemxaml"></a>Typy migrované z WPF do System.Xaml

V rozhraní .NET Framework 3.5 a .NET Framework 3.0 zahrnovaly nadace WPF (Windows Presentation Foundation) i Windows Workflow Foundation implementaci jazyka XAML. Mnoho veřejných typů, které zapředpokladu rozšiřitelnost pro implementaci WPF XAML existovaly v sestaveních WindowsBase, PresentationCore a PresentationFramework. Podobně veřejné typy, které poskytovaly rozšiřitelnost pro Windows Workflow Foundation XAML existovaly v sestavení System.Workflow.ComponentModel. V rozhraní .NET Framework 4 byly některé typy související s XAML migrovány do sestavení System.Xaml. Společná implementace rozhraní .NET Framework jazykových služeb XAML umožňuje mnoho scénářů rozšiřitelnosti XAML, které byly původně definovány implementací XAML konkrétního rozhraní, ale jsou nyní součástí celkové jazykové podpory rozhraní .NET Framework 4 XAML. Tento článek obsahuje seznam typů, které byly migrovány a popisuje problémy související s migrací.

## <a name="assemblies-and-namespaces"></a>Sestavení a obory názvů

V rozhraní .NET Framework 3.5 a .NET Framework 3.0 byly typy, které <xref:System.Windows.Markup> WPF implementoval pro podporu XAML, obecně v oboru názvů. Většina těchto typů byla v sestavení WindowsBase.

V rozhraní .NET Framework 4 <xref:System.Xaml> je nový obor názvů a nové sestavení System.Xaml. Mnoho typů, které byly původně implementovány pro WPF XAML jsou nyní k dispozici jako body rozšiřitelnosti nebo služby pro jakékoli implementace XAML. Jako součást jejich zpřístupnění pro obecnější scénáře jsou typy předávány typu z původního sestavení WPF do sestavení System.Xaml. To umožňuje scénáře rozšiřitelnosti XAML bez nutnosti zahrnout sestavení jiných architektur (například WPF a Windows Workflow Foundation).

U migrovaných typů zůstává většina <xref:System.Windows.Markup> typů v oboru názvů. To bylo částečně, aby se zabránilo přerušení mapování oboru názvů CLR v existujících implementacích na základě pro soubor. V důsledku toho <xref:System.Windows.Markup> obor názvů v rozhraní .NET Framework 4 obsahuje kombinaci obecných typů podpory jazyka XAML (ze sestavení System.Xaml) a typů, které jsou specifické pro implementaci WPF XAML (z WindowsBase a dalších sestavení WPF). Jakýkoli typ, který byl migrován do System.Xaml, ale existoval dříve v sestavení WPF, má podporu předávání typů ve verzi 4 sestavení WPF.

### <a name="workflow-xaml-support-types"></a>Typy podpory XAML pracovního postupu

Windows Workflow Foundation také za předpokladu, XAML typy podpory a v mnoha případech tyto měly identické krátké názvy ekvivalent WPF. Následuje seznam typů podpory XAML služby Windows Workflow Foundation:

- <xref:System.Workflow.ComponentModel.Serialization.ContentPropertyAttribute>

- <xref:System.Workflow.ComponentModel.Serialization.RuntimeNamePropertyAttribute>

- <xref:System.Workflow.ComponentModel.Serialization.XmlnsPrefixAttribute>

Tyto typy podpory stále existují v sestaveních Windows Workflow Foundation pro rozhraní .NET Framework 4 a lze je stále použít pro konkrétní aplikace Windows Workflow Foundation. však by neměly být odkazovány aplikace nebo architektury, které nepoužívají Windows Workflow Foundation.

## <a name="markupextension"></a>MarkupExtension

V rozhraních .NET Framework 3.5 a .NET Framework 3.0 byla <xref:System.Windows.Markup.MarkupExtension> třída wpf v sestavení WindowsBase. V sestavení System.Workflow.ComponentModel existovala paralelní třída pro založení <xref:System.Workflow.ComponentModel.Serialization.MarkupExtension>pracovního postupu systému Windows . V rozhraní .NET Framework <xref:System.Windows.Markup.MarkupExtension> 4 je třída migrována do sestavení System.Xaml. V rozhraní .NET <xref:System.Windows.Markup.MarkupExtension> Framework 4 je určen pro všechny scénáře rozšiřitelnosti XAML, který používá služby .NET XAML, nikoli pouze pro ty, které jsou na základě konkrétních architektur. Pokud je to možné, konkrétní rozhraní nebo uživatelský <xref:System.Windows.Markup.MarkupExtension> kód v rámci by měl také stavět na třídy pro rozšíření XAML.

## <a name="markupextension-supporting-service-classes"></a>Třídy podpůrné služby Značky Extension

Rozhraní .NET Framework 3.5 a .NET Framework 3.0 pro <xref:System.Windows.Markup.MarkupExtension> WPF <xref:System.ComponentModel.TypeConverter> poskytly několik služeb, které byly k dispozici implementátorům a implementacím pro podporu použití typu/vlastnosti v jazyce XAML. Tyto služby jsou následující:

- <xref:System.Windows.Markup.IProvideValueTarget>

- <xref:System.Windows.Markup.IUriContext>

- <xref:System.Windows.Markup.IXamlTypeResolver>

> [!NOTE]
> Další služba z rozhraní .NET Framework 3.5, která <xref:System.Windows.Markup.IReceiveMarkupExtension> souvisí s rozšířeními značek, je rozhraní. <xref:System.Windows.Markup.IReceiveMarkupExtension>nebyla migrována `[Obsolete]` a je označena pro rozhraní .NET Framework 4. Scénáře, které <xref:System.Windows.Markup.IReceiveMarkupExtension> dříve <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute> používaly by místo toho použít přiřazené zpětná volání. <xref:System.Windows.Markup.AcceptedMarkupExtensionExpressionTypeAttribute>je také `[Obsolete]`označena .

## <a name="xaml-language-features"></a>Funkce jazyka XAML

Několik funkcí jazyka XAML a komponent pro WPF dříve existovalo v sestavení PresentationFramework. Ty byly implementovány jako <xref:System.Windows.Markup.MarkupExtension> podtřída vystavit použití rozšíření značky v XAML značky. V rozhraní .NET Framework 4 existují v sestavení System.Xaml tak, aby projekty, které neobsahují sestavení WPF, mohly používat tyto funkce na úrovni jazyka XAML. WPF používá stejné implementace pro aplikace rozhraní .NET Framework 4. Stejně jako u ostatních případů, které jsou uvedeny v <xref:System.Windows.Markup> tomto tématu, podpůrné typy nadále existují v oboru názvů, aby se zabránilo porušení předchozí odkazy.

Následující tabulka obsahuje seznam tříd podpory funkcí XAML, které jsou definovány v souboru System.Xaml.

|Funkce jazyka XAML|Využití|
|---------------------------|-----------|
|<xref:System.Windows.Markup.ArrayExtension>|`<x:Array ...>`|
|<xref:System.Windows.Markup.NullExtension>|`{x:Null}`|
|<xref:System.Windows.Markup.StaticExtension>|`{x:Static ...}`|
|<xref:System.Windows.Markup.TypeExtension>|`{x:Type ...}`|

Přestože System.Xaml nemusí mít konkrétní třídy podpory, obecná logika pro zpracování jazykových funkcí pro jazyk XAML nyní sídlí v System.Xaml a jeho implementované xaml čtečky a autoři XAML. Například `x:TypeArguments` je atribut, který je zpracován programy XAML a zapisovateli XAML z implementací System.Xaml; lze poznamenat v datovém proudu uzlu XAML, má zpracování ve výchozím kontextu schématu XAML (clr), má reprezentaci typu systému XAML a tak dále. V důsledku toho je referenční dokumentace pro všechny funkce jazykové úrovně XAML dílčím tématem [pro služby XAML](../../../desktop-wpf/xaml-services/index.md) v [Průvodci pro stolní počítače pro Windows Presentation Foundation (WPF)](../../../desktop-wpf/overview/index.md).

## <a name="valueserializer-and-supporting-classes"></a>ValueSerializer a podpůrné třídy

Třída <xref:System.Windows.Markup.ValueSerializer> podporuje převod typu na řetězec, zejména pro případy serializace XAML, kde serializace může vyžadovat více režimů nebo uzlů ve výstupu. V rozhraních .NET Framework 3.5 a <xref:System.Windows.Markup.ValueSerializer> .NET Framework 3.0 byl pro WPF v sestavení WindowsBase. V rozhraní .NET Framework <xref:System.Windows.Markup.ValueSerializer> 4 je třída v System.Xaml a je určena pro všechny scénáře rozšiřitelnosti XAML, nikoli pouze pro ty, které jsou postaveny na WPF. <xref:System.Windows.Markup.IValueSerializerContext>(podpůrná služba) <xref:System.Windows.Markup.DateTimeValueSerializer> a (konkrétní podtřída) jsou také migrovány do System.Xaml.

## <a name="xaml-related-attributes"></a>Atributy související s XAML

WPF XAML zahrnuty několik atributů, které lze použít pro typy CLR k označení něco o jejich chování XAML. Následuje seznam atributů, které existovaly v sestaveních WPF v rozhraních .NET Framework 3.5 a .NET Framework 3.0. Tyto atributy jsou migrovány do souboru System.Xaml v rozhraní .NET Framework 4.

- <xref:System.Windows.Markup.AmbientAttribute>

- <xref:System.Windows.Markup.ContentPropertyAttribute>

- <xref:System.Windows.Markup.ContentWrapperAttribute>

- <xref:System.Windows.Markup.DependsOnAttribute>

- <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute>

- <xref:System.Windows.Markup.NameScopePropertyAttribute>

- <xref:System.Windows.Markup.RootNamespaceAttribute>

- <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>

- <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>

- <xref:System.Windows.Markup.ValueSerializerAttribute>

- <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>

- <xref:System.Windows.Markup.XmlLangPropertyAttribute>

- <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>

- <xref:System.Windows.Markup.XmlnsDefinitionAttribute>

- <xref:System.Windows.Markup.XmlnsPrefixAttribute>

## <a name="miscellaneous-classes"></a>Různé třídy

Rozhraní <xref:System.Windows.Markup.IComponentConnector> existovalo v rozhraních WindowsBase v rozhraních .NET Framework 3.5 a .NET Framework 3.0, ale existuje v souboru System.Xaml v rozhraní .NET Framework 4. <xref:System.Windows.Markup.IComponentConnector>je určen především pro podporu nástrojů a kompilátory značek XAML.

Rozhraní <xref:System.Windows.Markup.INameScope> existovalo v rozhraních WindowsBase v rozhraních .NET Framework 3.5 a .NET Framework 3.0, ale existuje v souboru System.Xaml v rozhraní .NET Framework 4. <xref:System.Windows.Markup.INameScope>definuje základní operace pro název rozsahu XAML.

## <a name="xaml-related-classes-with-shared-names-that-exist-in-wpf-and-systemxaml"></a>Třídy související s xAML se sdílenými názvy, které existují v WPF a System.Xaml

V sestaveních WPF i v sestavení System.Xaml v rozhraní .NET Framework 4 existují následující třídy:

`XamlReader`

`XamlWriter`

`XamlParseException`

Implementace WPF se nachází <xref:System.Windows.Markup> v oboru názvů a PresentationFramework sestavení. Implementace System.Xaml se nachází <xref:System.Xaml> v oboru názvů. Pokud používáte WPF typy nebo jsou odvozeny z WPF typy, obvykle byste <xref:System.Windows.Markup.XamlReader> měli <xref:System.Windows.Markup.XamlWriter> použít WPF implementace a namísto System.Xaml implementace. Další informace naleznete v <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> <xref:System.Windows.Markup.XamlWriter?displayProperty=nameWithType>tématu Poznámky v a .

Pokud jste včetně odkazy na sestavení WPF a System.Xaml a `include` také používáte příkazy pro <xref:System.Windows.Markup> oba a <xref:System.Xaml> obory názvů, budete muset plně kvalifikovat volání těchto rozhraní API k vyřešení typů bez nejasností.
