---
title: Třída XAMLServices a základní čtení a zápis v jazyku XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], XamlServices class
- XamlServices class [XAML Services], how to use
ms.assetid: 6ac27fad-3687-4d7a-add1-3e90675fdfde
ms.openlocfilehash: 27c7a45a45e8bbe3594813b29344d1548eecda5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565909"
---
# <a name="xamlservices-class-and-basic-xaml-reading-or-writing"></a>Třída XAMLServices a základní čtení a zápis v jazyku XAML
<xref:System.Xaml.XamlServices> je třída poskytuje rozhraní .NET Framework XAML Services, který můžete používat k adresování XAML scénáře, které nevyžadují konkrétním přístup k datový proud uzlu XAML, nebo XAML typ system informacemi získanými z těchto uzlů. <xref:System.Xaml.XamlServices> Rozhraní API jde vyhodnotit takto: `Load` nebo `Parse` pro podporu cestu zatížení XAML, `Save` pro podporu XAML cestu, uložení a `Transform` k poskytování technik, které připojuje cestu zatížení a uložit cestu. `Transform` Umožňuje změnit z jednoho schématu XAML do jiného. Toto téma shrnuje každý z těchto rozhraní API klasifikací a popisuje rozdíly mezi přetížení konkrétní metody.  
  
<a name="load"></a>   
## <a name="load"></a>Zatížení  
 Různé přetížení <xref:System.Xaml.XamlServices.Load%2A> implementovat dokončení logiku pro cestu k načtení. Cesta zatížení používá XAML v některé formuláře a výstupy datový proud uzlu XAML. Většina z nich načíst pomocí cesty XAML v kódované formě textového souboru XML. Ale můžete také načíst obecné datového proudu, nebo můžete načíst zdroj předem načtené XAML, který je už obsažený v jiné <xref:System.Xaml.XamlReader> implementace.  
  
 Nejjednodušší přetížení pro většinu scénářů je <xref:System.Xaml.XamlServices.Load%28System.String%29>. Toto přetížení má `fileName` parametr, který je jednoduše název textového souboru, který obsahuje XAML načíst. Toto je vhodná pro scénáře aplikací, jako jsou například aplikace úplný vztah důvěryhodnosti, které jste dříve serializovány stavu nebo data do místního počítače. To je užitečné pro rozhraní, kde jsou definování aplikačního modelu a chcete načíst jednu standardní soubory, které definuje chování aplikace, spuštění uživatelského rozhraní nebo jiné definované framework prostředky, které používají XAML.  
  
 <xref:System.Xaml.XamlServices.Load%28System.IO.Stream%29> má podobné scénáře. Toto přetížení může být užitečné, pokud máte uživatele, vyberte soubory načíst, protože <xref:System.IO.Stream> je často výstup jiné <xref:System.IO> rozhraní API, které můžete přístup k systému souborů. Nebo může být přístup k XAML zdrojů prostřednictvím asynchronní stahování nebo jiné sítě techniky, které také poskytují datového proudu. (Načítání z datového proudu nebo vybrané uživatelem zdroje může mít vliv na zabezpečení. Další informace najdete v tématu [aspekty zabezpečení XAML](../../../docs/framework/xaml-services/xaml-security-considerations.md).)  
  
 <xref:System.Xaml.XamlServices.Load%28System.IO.TextReader%29> a <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29> přetížení, které jsou závislé na čtečky formáty z předchozích verzí rozhraní .NET Framework. Pokud chcete použít tyto přetížení, můžete by měl už máte vytvořené čtečky instance a použít jeho `Create` rozhraní API načíst XAML v příslušném formuláři (text nebo XML). Pokud jste již přesunout záznam ukazatele v jiných čtečky nebo provést jiné operace s nimi, není to důležité. Cesta logiku zatížení z <xref:System.Xaml.XamlServices.Load%2A> vždy zpracuje celý XAML vstup z kořene dolů. Scénáře pro tyto přetížení mohl zahrnovat následující:  
  
-   Návrh povrchy, kde zadáte jednoduché XAML z existující text editoru XML specifické možnosti úprav.  
  
-   Variant jádra <xref:System.IO> scénáře, kde používáte vyhrazené čtečky otevřít soubory nebo datové proudy. Logika provede elementární kontrola nebo zpracování obsahu, než se pokusí načíst jako XAML.  
  
 Můžete buď načíst souboru nebo datový proud, nebo můžete načíst <xref:System.Xml.XmlReader>, <xref:System.IO.TextReader>, nebo <xref:System.Xaml.XamlReader> , zabalení váš vstup XAML načtením s rozhraními API program pro čtení.  
  
 Interně, každý z předchozí přetížení se nakonec <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29>a předaná <xref:System.Xml.XmlReader> se používá k vytvoření nové <xref:System.Xaml.XamlXmlReader>.  
  
 `Load` Podpisu, který poskytuje pokročilejší scénáře je <xref:System.Xaml.XamlServices.Load%28System.Xaml.XamlReader%29>. Můžete použít tento podpis pro jednu z následujících případech:  
  
-   Jste definovali vlastní implementaci <xref:System.Xaml.XamlReader>.  
  
-   Je třeba zadat nastavení pro <xref:System.Xaml.XamlReader> , se liší od výchozího nastavení.  
  
 Příkladem jiného než výchozího nastavení jsou nastavení žádné z následujících: <xref:System.Xaml.XamlReaderSettings.AllowProtectedMembersOnRoot%2A>; <xref:System.Xaml.XamlReaderSettings.BaseUri%2A>; <xref:System.Xaml.XamlReaderSettings.IgnoreUidsOnPropertyElements%2A>; <xref:System.Xaml.XamlReaderSettings.LocalAssembly%2A>; <xref:System.Xaml.XamlReaderSettings.ValuesMustBeString%2A>. Čtečka výchozí pro <xref:System.Xaml.XamlServices> je <xref:System.Xaml.XamlXmlReader>. Pokud jste zadali vlastní <xref:System.Xaml.XamlXmlReader>, s nastavením, jsou následující vlastnosti a nastavte jiné než výchozí <xref:System.Xaml.XamlXmlReaderSettings>: <xref:System.Xaml.XamlXmlReaderSettings.CloseInput%2A>; <xref:System.Xaml.XamlXmlReaderSettings.SkipXmlCompatibilityProcessing%2A>; <xref:System.Xaml.XamlXmlReaderSettings.XmlLang%2A>; <xref:System.Xaml.XamlXmlReaderSettings.XmlSpacePreserve%2A>.  
  
<a name="parse"></a>   
## <a name="parse"></a>analyzovat  
 <xref:System.Xaml.XamlServices.Parse%2A> je třeba `Load` vzhledem k tomu, že je cesta zatížení rozhraní API, které vytvoří datový proud uzlu XAML z jazyka XAML vstup. V takovém případě je však vstup XAML zadat přímo jako řetězec, který obsahuje všechny XAML načíst. <xref:System.Xaml.XamlServices.Parse%2A> je odlehčený přístup, který je pro scénáře aplikací vhodnější než framework scénáře. Další informace naleznete v tématu <xref:System.Xaml.XamlServices.Parse%2A>. <xref:System.Xaml.XamlServices.Parse%2A> je skutečně právě zabalené <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29> volání, které zahrnuje <xref:System.IO.StringReader> interně.  
  
<a name="save"></a>   
## <a name="save"></a>Uložit  
 Různé přetížení <xref:System.Xaml.XamlServices.Save%2A> implementovat Uložit cestu. Všechny <xref:System.Xaml.XamlServices.Save%2A> metody všechny trvat grafu objektu jako vstup a výstup jako datový proud, vytvořit soubor, nebo <xref:System.Xml.XmlWriter> / <xref:System.IO.TextWriter> instance.  
  
 Vstupní objekt musí být kořenový objekt některé reprezentace objektu. To může být jeden kořenový objektu firmy, kořenu stromu objekt pro stránku ve scénáři uživatelského rozhraní, pracovní plocha úpravy z nástroj návrhu nebo jiných kořenový objekt koncepty, které jsou vhodné pro scénáře.  
  
 V mnoha scénářích objekt stromové struktury, která jste uložili má vztah k původní operace, která načíst XAML, buď pomocí <xref:System.Xaml.XamlServices.Load%2A> nebo jiných rozhraní API implementované model framework nebo aplikace. Může být rozdíly zaznamenané v stromu objektů, které jsou z důvodu změny stavu, kde vaše aplikace zaznamenat nastavení běhového prostředí od uživatele, změny změnit XAML, protože je vaše aplikace XAML návrhu prostor, atd. S nebo bez změny konceptu prvního načítání XAML ze značek a znovu ho uložte a porovnání dvou formách značek XAML se někdy označuje jako odezvy reprezentace XAML.  
  
 Problém s ukládání a serializaci komplexní objekt, který je nastavený v podobě značek je rovnováhu mezi úplné reprezentace bez ztráty informací a podrobností, která vytváří XAML méně čitelná pro člověka. Kromě toho různých zákazníků pro jazyk XAML může mít jiné definice nebo očekávání pro nastavení tento odhad. <xref:System.Xaml.XamlServices.Save%2A> Rozhraní API představují jednu definici tento odhad. <xref:System.Xaml.XamlServices.Save%2A> Rozhraní API použijte k dispozici kontext schématu XAML a výchozí na základě CLR charakteristika <xref:System.Xaml.XamlType>, <xref:System.Xaml.XamlMember>, a další vnitřní XAML a XAML zadejte koncepty systému k určení, kde může být určité konstrukce datový proud uzlu XAML Optimalizovaná, když jsou uloženy zpět do kódu. Například <xref:System.Xaml.XamlServices> uložit cesty lze použít na základě CLR výchozí kontext schématu XAML k vyřešení <xref:System.Xaml.XamlType> pro objekty, můžete určit <xref:System.Xaml.XamlType.ContentProperty%2A?displayProperty=nameWithType>a pak můžete vynechat značky elementu vlastnost při zápisu vlastnost XAML obsahu objektu.  
  
<a name="transform"></a>   
## <a name="transform"></a>Transformace  
 <xref:System.Xaml.XamlServices.Transform%2A> Převede nebo transformuje XAML pomocí propojení cestu k načtení a uložení cestu jako jednu operaci. Zvolte jiné schéma kontext nebo jiné základní typ systému lze použít pro <xref:System.Xaml.XamlReader> a <xref:System.Xaml.XamlWriter>, který je co vliv, jak je transformovat výsledné XAML. To funguje dobře pro operace široký transformace.  
  
 Pro operace, které jsou závislé na každý uzel v datový proud uzlu XAML prozkoumání, obvykle použijete <xref:System.Xaml.XamlServices.Transform%2A>. Místo toho musíte definovat vlastní zatížení cesta ukládání cesta operace řady a interject vlastní logiky. V jednom z cest použijte pár XAML čtečky/XAML zapisovače kolem vlastní uzly smyčka. Například načíst počáteční XAML pomocí <xref:System.Xaml.XamlXmlReader> a krokování s vnořením uzly s následných <xref:System.Xaml.XamlXmlReader.Read%2A> volání. Operační na úrovni datový proud uzlu XAML můžete nyní upravit jednotlivé uzly (typy, členy, ostatní uzly) pro použití transformace, nebo nechte uzlu jako-je. Pak můžete poslat uzlu a vyšší odpovídajícího `Write` API <xref:System.Xaml.XamlObjectWriter> a zápisu objektu. Další informace najdete v tématu [struktury datový proud uzlu XAML principy a koncepty](../../../docs/framework/xaml-services/understanding-xaml-node-stream-structures-and-concepts.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xaml.XamlObjectWriter>  
 <xref:System.Xaml.XamlServices>  
 [XAML Services](../../../docs/framework/xaml-services/index.md)
