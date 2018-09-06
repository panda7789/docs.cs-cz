---
title: Podkladový kód a kód XAML v subsystému WPF
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], code-behind
- code-behind files [WPF], XAML
ms.assetid: 9df6d3c9-aed3-471c-af36-6859b19d999f
ms.openlocfilehash: ee08dc22588264b25d40b3fd818ef9ee1da90319
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "44032903"
---
# <a name="code-behind-and-xaml-in-wpf"></a>Podkladový kód a kód XAML v subsystému WPF
<a name="introduction"></a> Použití modelu Code-behind je pojem používaný pro kód, který je spojen s objekty definovanými značkami při [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránka není kompilována značka. Toto téma popisuje požadavky pro použití modelu code-behind i mechanismus alternativní vloženého kódu pro kód v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 Toto téma obsahuje následující oddíly:  
  
-   [Požadované součásti](#Prerequisites)  
  
-   [Použití modelu Code-Behind a jazyk XAML](#codebehind_and_the_xaml_language)  
  
-   [Použití modelu Code-behind, obslužná rutina události a požadavky na částečné třídy v subsystému WPF](#Code_behind__Event_Handler__and_Partial_Class)  
  
-   [x: Code](#x_Code)  
  
-   [Omezení vloženého kódu](#Inline_Code_Limitations)  
  
<a name="Prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 Toto téma předpokládá, že jste četli [přehled XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md) a mají některé základní znalosti o [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] a objektově orientované programování.  
  
<a name="codebehind_and_the_xaml_language"></a>   
## <a name="code-behind-and-the-xaml-language"></a>Použití modelu Code-Behind a jazyk XAML  
 Jazyk XAML obsahuje funkce na úrovni jazyka, které umožňují přidružit soubory kódu značek souborů ze strany soubor značek. Konkrétně jazyka XAML definuje jazykové funkce [x: Class – direktiva](../../../../docs/framework/xaml-services/x-class-directive.md), [x: Subclass – direktiva](../../../../docs/framework/xaml-services/x-subclass-directive.md), a [x: ClassModifier – direktiva](../../../../docs/framework/xaml-services/x-classmodifier-directive.md). Přesně jak by se měly vytvářet kód a jak integrovat značek a kódu, není součástí co určuje jazyka XAML. Je ponecháno architektury, jako jsou WPF a zjistěte, jak integrovat kódu, jak používat XAML v aplikaci a programovacích modelů a sestavení akce nebo jiné podpory, který to vše vyžaduje.  
  
<a name="Code_behind__Event_Handler__and_Partial_Class"></a>   
## <a name="code-behind-event-handler-and-partial-class-requirements-in-wpf"></a>Použití modelu Code-behind, obslužná rutina události a požadavky na částečné třídy v subsystému WPF  
  
-   Částečné třídy musí být odvozen od typu, který zálohuje kořenový element.  
  
-   Všimněte si, že v rámci výchozího chování akce sestavení kompilace kódu, můžete ponechat odvození prázdné v definici dílčí třídy na straně použití modelu code-behind. I v případě, že není zadán, bude předpokládat zkompilovaného výsledku základní typ stránky kořenový jako základ pro částečné třídy. Ale spoléhání se na toto chování není nejvhodnější.  
  
-   Obslužné rutiny událostí, který píšete v modelu code-behind musejí být metody instance a nemůže být statické metody. Tyto metody musí být určené částečné třídy v oboru názvů CLR identifikovaný `x:Class`. Nemůže kvalifikovat název obslužné rutiny události dáte pokyn, aby [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesoru hledat obslužné rutiny události pro propojování událostí v oboru jinou třídu.  
  
-   Obslužná rutina musí odpovídat delegáta pro odpovídající události v systému typů zálohování.  
  
-   Pro jazyk Microsoft Visual Basicu konkrétně, můžete použít konkrétní jazyk `Handles` – klíčové slovo přidružit instance a události v deklaraci obslužné rutiny místo připojování obslužné rutiny s atributy v obslužné rutiny [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Tento postup však mají určitá omezení, protože `Handles` – klíčové slovo nemůže podporovat všechny konkrétní funkce [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] systém událostí, jako je například určité směrují scénářů událostí nebo připojených událostí. Podrobnosti najdete v tématu [jazyka Visual Basic a WPF zpracování událostí](../../../../docs/framework/wpf/advanced/visual-basic-and-wpf-event-handling.md).  
  
<a name="x_Code"></a>   
## <a name="xcode"></a>x: Code  
 [x: Code](../../../../docs/framework/xaml-services/x-code-intrinsic-xaml-type.md) je definován prvek direktiv v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. `x:Code` Direktivu element může obsahovat vložené programového kódu. Kód, který je definována vložením může zasahovat [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] na stejné stránce. Následující příklad ukazuje vnořeného kódu C#. Všimněte si, že kód je uvnitř `x:Code` element a že kód musejí být uzavřeny do `<CDATA[`... `]]>` k uvození obsah pro [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]tak, aby [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesoru (interpretace buď [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] schématu nebo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] schéma), nedojde k interpretaci obsah doslova jako [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)].  
  
 [!code-xaml[XAMLOvwSupport#ButtonWithInlineCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page4.xaml#buttonwithinlinecode)]  
  
<a name="Inline_Code_Limitations"></a>   
## <a name="inline-code-limitations"></a>Omezení vloženého kódu  
 Měli byste zvážit vyloučení nebo omezení využití vloženého kódu. Z hlediska architekturu a kódování filozofií udržování oddělení mezi značky a modelu code-behind udržuje role návrháři a vývojáři mnohem více jedinečných. Na další odborné úrovni, může být není vhodný pro zápis, kód, který napíšete pro vložený kód protože jsou vždy zápisu do [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] generované částečné třídy a mohou používat pouze výchozí mapování názvového prostoru XML. Protože nemůžete přidat `using` příkazy, které musí plnému řadu [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] volání, které jste provedli. Výchozí hodnota [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mapování obsahují nejvíce, ale ne všechny [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] obory názvů, které se nacházejí v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sestavení; bude mít k plnému určení volání k typům a členům obsažené v jiných oborech názvů CLR. Také nelze definovat nic nad rámec částečné třídy v vloženého kódu a všechny entity kód uživatele, který odkazujete, musí existovat jako členové nebo proměnné v rámci vygenerovanou dílčí třídu. Další programovací funkcí, například makra nebo `#ifdef` před globální proměnné a proměnné sestavení nejsou k dispozici. Další informace najdete v tématu [x: Code vnitřního typu XAML](../../../../docs/framework/xaml-services/x-code-intrinsic-xaml-type.md).  
  
## <a name="see-also"></a>Viz také  
 [Přehled XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [x:Code – vnitřní typ jazyka XAML](../../../../docs/framework/xaml-services/x-code-intrinsic-xaml-type.md)  
 [Sestavení aplikace WPF](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)  
 [Podrobná syntaxe XAML](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)
