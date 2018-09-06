---
title: Serializace a úložiště dokumentu
ms.date: 03/30/2017
helpviewer_keywords:
- 'serialization of documents [WPF], , '
- documents [WPF], storage
- documents [WPF], serialization
ms.assetid: 4839cd87-e206-4571-803f-0200098ad37b
ms.openlocfilehash: 39466eb528003e36bfa05751f83619d86b78a2a7
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43798768"
---
# <a name="document-serialization-and-storage"></a>Serializace a úložiště dokumentu
Microsoft .NET Framework poskytuje výkonné prostředí pro vytváření a zobrazování vysoce kvalitní dokumenty.  Rozšířené funkce, které podporují – dokumenty a tok dokumenty, rozšířené zobrazení ovládacích prvků, v kombinaci s výkonné 2D a 3D grafické možnosti trvat aplikace rozhraní .NET Framework na zcela novou úroveň kvality a činnost koncového uživatele.  Dokáže flexibilně spravovat v paměti reprezentace dokumentu je klíčovou funkcí rozhraní .NET Framework a nebudou moct efektivně ukládat a načítat dokumenty z úložiště dat je potřeba téměř všechny aplikace.  Proces převodu dokumentu z interního vyjádření v paměti k externím úložišti, se nazývá serializace.  Proces zpětné čtení úložiště dat a znovu vytvořit původní instance v paměti je označován deserializace.  
  
 
  
<a name="AboutSerialization"></a>   
## <a name="about-document-serialization"></a>Informace o serializaci dokumentu  
 V ideálním případě je proces serializaci a deserializaci dokumentu z a potom zpět do paměti pro aplikace transparentní.  Aplikace volá serializátor "write" metody uložte dokument, zatímco deserializátor "číst" metoda přistupuje k úložišti dat a obnoví původní instance v paměti.  Určitý formát, který jsou data uložená v nehrají důležitou obecně aplikace, stejně jako jako serializace a deserializace proces znovu vytvoří dokument zpět na původní podobě.  
  
 Aplikace často poskytují více možností serializace, které uživateli umožňují uložit dokumenty do různých média nebo do jiného formátu.  Aplikace může například nabízejí možnosti "Uložit jako" ukládání dokumentu na disku, databáze nebo webové službě.  Podobně může uchovávat různé serializátory dokumentu v různých formátech, jako v HTML, formátu RTF, XML, XPS, nebo můžete také do jiného formátu.  Serializace do aplikace, definuje rozhraní, který izoluje podrobnosti paměťovému médiu v rámci implementace každé konkrétní serializátor.  Kromě přínosů zapouzdření podrobnosti o úložišti, rozhraní .NET Framework <xref:System.Windows.Documents.Serialization> [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] poskytují několik dalších důležitých funkcí.  
  
### <a name="features-of-net-framework-30-document-serializers"></a>Funkce rozhraní .NET Framework 3.0 dokumentu Serializátorů  
  
-   Přímý přístup k objektům vysoké úrovně dokumentu (Logická stromová struktura a vizuály) umožňují efektivní úložiště stránkované obsahu, 2D a 3D elementů, obrázky, média, hypertextové odkazy, poznámky a další obsah podpory.  
  
-   Synchronní a asynchronní operace.  
  
-   Podpora pro modul plug-in serializátory s rozšířenými funkcemi:  
  
    -   Systémová přístup pro použití u všech aplikací rozhraní .NET Framework.  
  
    -   Modul plug-in zjistitelnost jednoduchou aplikaci.  
  
    -   Jednoduché nasazení, instalace a aktualizace pro vlastní moduly plug-in třetích stran.  
  
    -   Podpora uživatelského rozhraní pro vlastní nastavení za běhu a možnosti.  
  
### <a name="xps-print-path"></a>Cesta tisku XPS  
 Rozhraní Microsoft .NET Framework [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] cesta tisku také poskytuje rozšířitelný mechanismus pro psaní dokumenty tiskový výstup.  [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] slouží jako formát souboru dokument a je formát nativní zařazování tisku pro [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)].  [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] dokumenty můžete odeslat přímo do [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]– bez nutnosti pro převod na mezilehlého formátu kompatibilním s airprintem.  Zobrazit [přehled tisku s](../../../../docs/framework/wpf/advanced/printing-overview.md) Další informace o možnostech výstupní cesta tisku a funkcích.  
  
<a name="PluginSerializers"></a>   
## <a name="plug-in-serializers"></a>Modul plug-in Serializátorů  
 <xref:System.Windows.Documents.Serialization> Rozhraní API poskytuje podporu pro modul plug-in serializátory a propojené serializátory, které se instalují samostatně z aplikace, vytvořit vazbu za běhu a jsou přístupné pomocí <xref:System.Windows.Documents.Serialization.SerializerProvider> mechanismus zjišťování.  Modul plug-in serializátory nabízejí rozšířené výhody pro snadné nasazení a použití celý systém.  Propojené serializátory může být také implementováno pro prostředí částečným vztahem důvěryhodnosti jako [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] kde modulu plug-in serializátory nejsou dostupné.  Propojené serializátory, které jsou založeny na odvozené provádění <xref:System.Windows.Documents.Serialization.SerializerWriter> třídy, jsou zkompilovány a propojeny přímo do aplikace.  Modul plug-in serializátory a propojené serializátory pracovat prostřednictvím stejné veřejné metody a události, které usnadňují použití jednoho nebo obou druhů serializátory ve stejné aplikaci.  
  
 Modul plug-in serializátory podpory vývojářům aplikací tím, že poskytuje rozšíření pro nové návrhy úložiště a formátů souborů, aniž byste museli kód přímo pro každý potenciální formátu v okamžiku sestavení.  Modul plug-in serializátory taky využívat vývojáři třetích stran tím, že poskytuje standardizované způsob, jak nasadit, instalace a aktualizace systému dostupný moduly plug-in pro vlastní nebo chráněných formátů.  
  
### <a name="using-a-plug-in-serializer"></a>Pomocí modulu Plug-in serializátoru  
 Modul plug-in serializátory snadno se používá.  <xref:System.Windows.Documents.Serialization.SerializerProvider> Vytvoří výčet tříd <xref:System.Windows.Documents.Serialization.SerializerDescriptor> objekt pro každý modul plug-in nainstalovat v systému.  <xref:System.Windows.Documents.Serialization.SerializerDescriptor.IsLoadable%2A> Vlastnost filtruje nainstalované moduly plug-in závisí na aktuální konfiguraci a ověří, zda serializátoru, který lze načíst a používané aplikace.  <xref:System.Windows.Documents.Serialization.SerializerDescriptor> Poskytuje také další vlastnosti, jako například <xref:System.Windows.Documents.Serialization.SerializerDescriptor.DisplayName%2A> a <xref:System.Windows.Documents.Serialization.SerializerDescriptor.DefaultFileExtension%2A>, které může aplikace použít uživatele při výběru serializátoru pro výstupní formát.  Výchozí modul plug-in serializátor pro [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] je součástí rozhraní .NET Framework a je vždy ve výčtu.  Když uživatele vybere výstupní formát, <xref:System.Windows.Documents.Serialization.SerializerProvider.CreateSerializerWriter%2A> metoda se používá k vytvoření <xref:System.Windows.Documents.Serialization.SerializerWriter> pro konkrétní formát.  <xref:System.Windows.Documents.Serialization.SerializerWriter>.<xref:System.Windows.Documents.Serialization.SerializerWriter.Write%2A> metodu lze volat pak do výstupního datového proudu dokumentu k úložišti.  
  
 Následující příklad ukazuje aplikace, která se používá <xref:System.Windows.Documents.Serialization.SerializerProvider> metoda ve vlastnosti "PlugInFileFilter".  PlugInFileFilter vytvoří výčet nainstalovaných modulů plug-in a sestaví řetězec filtru možnosti k dispozici soubor <xref:Microsoft.Win32.SaveFileDialog>.  
  
 [!code-csharp[DocumentSerialize#DocSerializeFileFilter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DocumentSerialize/CSharp/ThumbViewer.cs#docserializefilefilter)]  
  
 Po výběru název výstupního souboru tímto uživatelem, následující příklad ukazuje použití metody <xref:System.Windows.Documents.Serialization.SerializerProvider.CreateSerializerWriter%2A> metody pro ukládání daný dokument v zadaném formátu.  
  
 [!code-csharp[DocumentSerialize#DocSerializePlugIn](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DocumentSerialize/CSharp/ThumbViewer.cs#docserializeplugin)]  
  
<a name="InstallingPluginSerializers"></a>   
### <a name="installing-plug-in-serializers"></a>Instalace modulu Plug-in Serializátorů  
 <xref:System.Windows.Documents.Serialization.SerializerProvider> Třída poskytuje vyšší úrovně rozhraní pro modul plug-in serializátor zjišťování a přístup.  <xref:System.Windows.Documents.Serialization.SerializerProvider> Vyhledá a poskytuje aplikace seznam serializátory, které jsou nainstalované a dostupné v systému.  Specifika nainstalovaných serializátory se definují pomocí nastavení registru.  Modul plug-in serializátory lze přidat do registru pomocí <xref:System.Windows.Documents.Serialization.SerializerProvider.RegisterSerializer%2A> metoda; nebo pokud rozhraní .NET Framework není ještě nainstalována, skript instalace modulu plug-in lze přímo nastavit hodnoty registru samotný.  <xref:System.Windows.Documents.Serialization.SerializerProvider.UnregisterSerializer%2A> Metodu je možné odebrat dříve nainstalovaných modulů plug-in, nebo nastavení registru mají resetovat podobně skript pro odinstalaci.  
  
### <a name="creating-a-plug-in-serializer"></a>Vytvoření modulu Plug-in serializátoru  
 Modul plug-in serializátory a propojené serializátory použít stejné vystavené veřejné metody a události a podobně může být navržené pro provozování synchronně nebo asynchronně.  Existují tři základní kroky, které jsou obvykle používá k vytvoření modulu plug-in serializátoru:  
  
1.  Implementace a ladění serializátoru, který je první jako propojené serializátor.  Zpočátku vytvoření serializátoru, který je zkompilovány a propojeny přímo v aplikaci test poskytuje úplný přístup ke zarážky a další užitečné ladění služby pro účely testování.  
  
2.  Poté, co byl plně testovaný serializátoru, <xref:System.Windows.Documents.Serialization.ISerializerFactory> rozhraní se přidá k vytvoření modulu plug-in.  <xref:System.Windows.Documents.Serialization.ISerializerFactory> Rozhraní umožňuje úplný přístup ke všem objektům rozhraní .NET Framework, která obsahuje logický strom, nepoužívejte <xref:System.Windows.UIElement> objekty, <xref:System.Windows.Documents.IDocumentPaginatorSource>, a <xref:System.Windows.Media.Visual> elementy.  Kromě toho <xref:System.Windows.Documents.Serialization.ISerializerFactory> poskytuje stejné synchronní a asynchronní metody a události používané propojené serializátory.  Protože velkých dokumentů může trvat dobu výstup, asynchronních operací se doporučuje udržovat responzivní uživatelské interakce a nabídky možnost "Storno", pokud dojde k nějakému problému s úložištěm dat.  
  
3.  Po vytvoření modulu plug-in serializátor instalačního skriptu je implementován pro distribuci a instalaci (a odinstalaci) modulu plug-in (viz výše, "[instalace modulu Plug-in Serializátory](#InstallingPluginSerializers)").  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Documents.Serialization>  
 <xref:System.Windows.Xps.XpsDocumentWriter>  
 <xref:System.Windows.Xps.Packaging.XpsDocument>  
 [Dokumenty v platformě WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Přehled tisku](../../../../docs/framework/wpf/advanced/printing-overview.md)  
 [XML Paper Specification: Přehled](https://go.microsoft.com/fwlink?LinkID=106246)
