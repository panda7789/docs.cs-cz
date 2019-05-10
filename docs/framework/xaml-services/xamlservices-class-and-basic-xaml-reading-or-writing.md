---
title: Třída XAMLServices a základní čtení a zápis v jazyku XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], XamlServices class
- XamlServices class [XAML Services], how to use
ms.assetid: 6ac27fad-3687-4d7a-add1-3e90675fdfde
ms.openlocfilehash: a47436d9f7df099f54d450f6f8176b8cba6d7f5d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64622899"
---
# <a name="xamlservices-class-and-basic-xaml-reading-or-writing"></a>Třída XAMLServices a základní čtení a zápis v jazyku XAML
<xref:System.Xaml.XamlServices> je třída poskytuje rozhraní .NET Framework XAML Services, který slouží k řešení scénářů XAML, které nevyžadují žádná zvláštní přístup k datový proud uzlu XAML nebo XAML typu systémové informace získané z těchto uzlů. <xref:System.Xaml.XamlServices> Rozhraní API jde vyhodnotit takto: `Load` nebo `Parse` pro podporu zatížení cestu XAML `Save` k podpoře XAML cestu, uložení a `Transform` k poskytování technika, která připojí načíst cestu a uložit cestu. `Transform` je možné změnit z jednoho schématu XAML do jiného. Toto téma shrnuje každého z těchto klasifikací rozhraní API a popisuje rozdíly mezi konkrétní metody přetížení.  
  
<a name="load"></a>   
## <a name="load"></a>Načítání  
 Různé přetížení <xref:System.Xaml.XamlServices.Load%2A> implementovat kompletní logiku pro cestu zatížení. Načíst cestu používá v nějaké podobě XAML a vrací datový proud uzlu XAML. Většina z nich načíst pomocí cesty XAML v kódované podobě textového souboru XML. Ale můžete také načíst obecné datového proudu nebo můžete načíst přednačtené zdroje XAML, který je již obsažen v jiné <xref:System.Xaml.XamlReader> implementace.  
  
 Nejjednodušší přetížení pro většinu scénářů je <xref:System.Xaml.XamlServices.Load%28System.String%29>. Toto přetížení má `fileName` parametr, který je jednoduše název textového souboru, který obsahuje XAML pro načtení. Je to vhodné pro scénáře aplikací, jako jsou třeba aplikace úplný vztah důvěryhodnosti, které jste dříve serializovat data na místním počítači nebo stav. To je užitečné pro rozhraní, když definujete model aplikace a chcete načíst jeden ze standardních souborů, které definuje chování aplikace, od uživatelského rozhraní nebo další funkce definované v rámci rozhraní, které používají XAML.  
  
 <xref:System.Xaml.XamlServices.Load%28System.IO.Stream%29> obsahuje podobné scénáře. Toto přetížení může být užitečné, pokud máte uživatele, vyberte soubory, které chcete načíst, protože <xref:System.IO.Stream> je často výstup jiných <xref:System.IO> rozhraní API, která může získat přístup k systému souborů. Nebo může být přístup k zdroje XAML prostřednictvím asynchronní stahování nebo jiné sítě techniky, které poskytují také datového proudu. (Načítání z datového proudu nebo uživatel vybral zdroj může mít vliv na zabezpečení. Další informace najdete v tématu [aspekty zabezpečení XAML](xaml-security-considerations.md).)  
  
 <xref:System.Xaml.XamlServices.Load%28System.IO.TextReader%29> a <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29> přetížení, které využívají čtenáři formáty z předchozích verzí rozhraní .NET Framework. Chcete-li použít tato přetížení, by měl máte již vytvořena instance reader a použít jeho `Create` rozhraní API k načtení XAML v příslušném formuláři (textu nebo XML). Pokud již máte záznam ukazatele přesunutého jinými čtenáři nebo provádění jiných operací s nimi, není to důležité. Cesta logiky zatížení z <xref:System.Xaml.XamlServices.Load%2A> vždy zpracuje celý XAML vstup z kořenového adresáře dolů. Scénáře pro tato přetížení mohl zahrnovat následující:  
  
- Návrh povrchy kde poskytuje jednoduché možnosti z existující textový editor XML-konkrétní úprav XAML.  
  
- Varianty jádro <xref:System.IO> scénáře, kdy použít vyhrazený čtenáři k otevření souborů nebo datových proudů. Logiky provede základní kontrolu nebo zpracování obsahu, než se pokusí načíst jako XAML.  
  
 Můžete načíst soubor nebo datového proudu nebo můžete načíst <xref:System.Xml.XmlReader>, <xref:System.IO.TextReader>, nebo <xref:System.Xaml.XamlReader> , zabalit váš vstup XAML načtením s rozhraními API pro čtenáře.  
  
 Interně, každý z předchozích přetížení v konečném důsledku je <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29>, předanému <xref:System.Xml.XmlReader> slouží k vytvoření nového <xref:System.Xaml.XamlXmlReader>.  
  
 `Load` Signaturou, které poskytuje pokročilejší scénáře jsou <xref:System.Xaml.XamlServices.Load%28System.Xaml.XamlReader%29>. Tento podpis slouží pro jednu z následujících případech:  
  
- Jste definovali vlastní implementaci <xref:System.Xaml.XamlReader>.  
  
- Je třeba zadat nastavení pro <xref:System.Xaml.XamlReader> , která se liší od výchozího nastavení.  
  
 Příkladem jiného než výchozího nastavení jsou nastavení některý z následujících akcí: <xref:System.Xaml.XamlReaderSettings.AllowProtectedMembersOnRoot%2A>; <xref:System.Xaml.XamlReaderSettings.BaseUri%2A>; <xref:System.Xaml.XamlReaderSettings.IgnoreUidsOnPropertyElements%2A>; <xref:System.Xaml.XamlReaderSettings.LocalAssembly%2A>; <xref:System.Xaml.XamlReaderSettings.ValuesMustBeString%2A>. Výchozí čtecí zařízení pro <xref:System.Xaml.XamlServices> je <xref:System.Xaml.XamlXmlReader>. Pokud zadáte vlastní <xref:System.Xaml.XamlXmlReader>, s nastaveními, toto jsou vlastnosti, které chcete nastavit jiné výchozí <xref:System.Xaml.XamlXmlReaderSettings>: <xref:System.Xaml.XamlXmlReaderSettings.CloseInput%2A>; <xref:System.Xaml.XamlXmlReaderSettings.SkipXmlCompatibilityProcessing%2A>; <xref:System.Xaml.XamlXmlReaderSettings.XmlLang%2A>; <xref:System.Xaml.XamlXmlReaderSettings.XmlSpacePreserve%2A>.  
  
<a name="parse"></a>   
## <a name="parse"></a>Analýzy  
 <xref:System.Xaml.XamlServices.Parse%2A> je třeba `Load` vzhledem k tomu, že je načíst cestu rozhraní API, které vytvoří datový proud uzlu XAML ze vstupu XAML. Ale v takovém případě vstup XAML je k dispozici přímo jako řetězec, který obsahuje všechny XAML pro načtení. <xref:System.Xaml.XamlServices.Parse%2A> je odlehčený přístup, který je vhodnější pro scénáře aplikací než framework scénáře. Další informace naleznete v tématu <xref:System.Xaml.XamlServices.Parse%2A>. <xref:System.Xaml.XamlServices.Parse%2A> je vlastně jenom zabalené <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29> volání, které zahrnuje <xref:System.IO.StringReader> interně.  
  
<a name="save"></a>   
## <a name="save"></a>Uložit  
 Různé přetížení <xref:System.Xaml.XamlServices.Save%2A> implementovat Uložit cestu. Všechny <xref:System.Xaml.XamlServices.Save%2A> souboru provést všechny grafu objektu jako vstup a výstup jako datový proud, metody nebo <xref:System.Xml.XmlWriter> / <xref:System.IO.TextWriter> instance.  
  
 Vstupní objekt očekává se kořenový objekt některé reprezentaci objektu. To může být jeden kořenový objekt obchodní kořen stromu objektů pro stránku ve scénáři uživatelského rozhraní, pracovní plocha úpravy návrhářský nástroj nebo dalších pojmech kořenový objekt, které jsou vhodné pro scénáře.  
  
 V mnoha scénářích strom objektů, které uložíte má vztah k původní operace, která načíst XAML s <xref:System.Xaml.XamlServices.Load%2A> nebo jiné rozhraní API implementované rozhraní framework/aplikačního modelu. Mohou existovat rozdíly zachycené v rámci stromů objektů, které jsou z důvodu změny stavu, kde aplikace zachycené nastavení běhového prostředí od uživatele, změny změnit XAML, protože aplikace XAML návrhu surface, atd. S nebo bez změny konceptu první načítání XAML v označení a znovu ho uložte a porovnání dvě různými formami značky XAML se někdy označuje jako operace round-trip reprezentace XAML.  
  
 Výzvy k ukládání a serializaci komplexní objekt, který je nastaven v podobě značek se dosahuje rovnováhy mezi úplnou reprezentaci bez ztráty informací a úroveň podrobností, která provádí XAML méně čitelné. Kromě toho různých zákazníků pro XAML může mít jiné definice nebo očekávání pro nastavení toto rozdělení. <xref:System.Xaml.XamlServices.Save%2A> Rozhraní API představují jednu definici toto rozdělení. <xref:System.Xaml.XamlServices.Save%2A> Rozhraní API používají k dispozici kontext schématu XAML a výchozí na základě CLR charakteristiky <xref:System.Xaml.XamlType>, <xref:System.Xaml.XamlMember>, a další vnitřní XAML a XAML zadejte koncepty systému k určení, kde může být určité konstrukce datový proud uzlu XAML Optimalizované uložení zpět do kódu. Například <xref:System.Xaml.XamlServices> uložit cesty lze použít na základě CLR výchozí kontext schématu XAML k vyřešení <xref:System.Xaml.XamlType> pro objekty, můžete zjistit <xref:System.Xaml.XamlType.ContentProperty%2A?displayProperty=nameWithType>a pak můžete vynechat značky elementů vlastnost při zápisu vlastnost obsahu objektu XAML.  
  
<a name="transform"></a>   
## <a name="transform"></a>Transformace  
 <xref:System.Xaml.XamlServices.Transform%2A> Převede nebo transformuje XAML propojením načíst cestu a uložit cestu jako jediná operace. Kontext jiné schéma nebo záložní systém typů lze použít pro <xref:System.Xaml.XamlReader> a <xref:System.Xaml.XamlWriter>, což je, co ovlivňuje, jak transformovat výsledný XAML. Tento postup funguje dobře pro operace široké transformace.  
  
 Pro operace, které spoléhají na každý uzel v datovém proudu uzlu XAML zkoumání, obvykle použijete <xref:System.Xaml.XamlServices.Transform%2A>. Místo toho budete muset definovat vlastní zatížení cesta Uložit cestu operace řady a interject vlastní logiku. Jedním z cest použijte pár XAML čtečky/XAML zapisovače kolem uzlů smyčku. Například načtení počáteční XAML pomocí <xref:System.Xaml.XamlXmlReader> a krokování s vnořením do uzlů s po sobě jdoucích <xref:System.Xaml.XamlXmlReader.Read%2A> volání. Provozování na úrovni datový proud uzlu XAML teď můžete upravit jednotlivé uzly (typy, členy, ostatní uzly) Chcete-li použít transformace, nebo ponechejte uzel jako-je. Pak odešlete uzlu a vyšší příslušné `Write` rozhraní API <xref:System.Xaml.XamlObjectWriter> a vypsat objektu. Další informace najdete v tématu [Principy XAML Stream struktur a koncepcí uzlů](understanding-xaml-node-stream-structures-and-concepts.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xaml.XamlObjectWriter>
- <xref:System.Xaml.XamlServices>
- [XAML Services](index.md)
