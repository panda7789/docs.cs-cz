---
title: Serializace a úložiště dokumentu
ms.date: 03/30/2017
helpviewer_keywords:
- 'serialization of documents [WPF], , '
- documents [WPF], storage
- documents [WPF], serialization
ms.assetid: 4839cd87-e206-4571-803f-0200098ad37b
ms.openlocfilehash: 8ee8acb95aa4a7c8dd80ea88594e582f05b71611
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33546676"
---
# <a name="document-serialization-and-storage"></a>Serializace a úložiště dokumentu
Rozhraní Microsoft .NET Framework poskytuje výkonné prostředí pro vytváření a zobrazování dokumentů vysoké kvality.  Rozšířené funkce, které podporují – dokumenty a toku dokumenty, rozšířené zobrazení ovládacích prvků, v kombinaci s efektivní 2D a 3D grafický funkce trvat aplikací rozhraní .NET Framework na novou úroveň kvality a činnost koncového uživatele.  Schopnost spravovat flexibilně reprezentaci v paměti dokumentu je klíčovou funkcí rozhraní .NET Framework a schopnost efektivně uložení a načtení dokumenty z jiného úložiště dat je zapotřebí téměř každé aplikace.  Proces převodu dokument k úložišti externí data z interního vyjádření v paměti se říká serializace.  Proces zpětné čtení úložiště dat a znovu vytvořit na původní instanci v paměti se říká deserializace.  
  
 
  
<a name="AboutSerialization"></a>   
## <a name="about-document-serialization"></a>O serializaci dokumentu  
 V ideálním případě proces serializaci a deserializaci dokumentu z a potom zpět do paměti je transparentní pro aplikace.  Aplikace volá označuje, že serializátor "zápisu" metoda uložit do dokumentu deserializátor "číst" metoda přistupuje k úložišti dat a znovu vytvoří na původní instanci v paměti.  Konkrétní formát, který jsou data uložená v není obecně důležité aplikace jako dlouhé jako serializace a deserializace procesu vytvoří dokument zpět na původní podobě.  
  
 Aplikace často poskytují více možností serializace, které uživateli umožňují uložit dokumenty, jiný střední nebo do jiného formátu.  Aplikace může například nabízí možnosti "Uložit jako" ukládání dokument soubor na disku, databáze nebo webové službě.  Podobně různých serializátorů může ukládat dokumentu v různých formátech, jako v HTML, RTF, XML, XPS nebo případně do formátu třetích stran.  Do aplikace definuje serializace rozhraní, které izoluje podrobnosti střední úložiště v rámci provádění jednotlivých konkrétní serializátor.  Kromě výhod zapouzdřením podrobnosti úložiště, rozhraní .NET Framework <xref:System.Windows.Documents.Serialization> [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] poskytují několik důležitých funkcí.  
  
### <a name="features-of-net-framework-30-document-serializers"></a>Funkce rozhraní .NET Framework 3.0 dokumentu Serializátorů  
  
-   Přímý přístup k objektům vysoké úrovně dokumentu (logického stromu a vizuální prvky) povolte efektivní úložiště stránkované obsahu, 2D/3D elementů, obrázky, média, hypertextové odkazy, poznámky a jiný obsah podpory.  
  
-   Synchronní a asynchronní operace.  
  
-   Podpora pro modul plug-in serializátorů s rozšířenými možnostmi:  
  
    -   Systémové přístup pro použití ve všech aplikací rozhraní .NET Framework.  
  
    -   Modul plug-in zjistitelnost jednoduchou aplikaci.  
  
    -   Jednoduché nasazení, instalace a aktualizace vlastní plug-in jiných výrobců.  
  
    -   Podpora uživatelské rozhraní pro vlastní nastavení spuštění a možnosti.  
  
### <a name="xps-print-path"></a>Cesta pro tisk XPS  
 Rozhraní Microsoft .NET Framework [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] tiskové cesta také poskytuje rozšiřitelný mechanismus pro zápis dokumentů prostřednictvím tiskový výstup.  [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] slouží jako obou dokumentu formát souboru a je nativní zařazování tisku formát [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)].  [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] dokumenty můžete odeslat přímo na [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]-kompatibilní tiskárny bez nutnosti pro převod do formátu zprostředkující.  Najdete v článku [přehled tisku](../../../../docs/framework/wpf/advanced/printing-overview.md) Další informace o tiskových cestu výstupního možnostech a funkcích.  
  
<a name="PluginSerializers"></a>   
## <a name="plug-in-serializers"></a>Modul plug-in Serializátorů  
 <xref:System.Windows.Documents.Serialization> Rozhraní API poskytuje podporu pro modul plug-in serializátorů a propojené serializátorů, které se instalují samostatně z aplikace, vazby v době běhu a ke kterým se přistupuje pomocí <xref:System.Windows.Documents.Serialization.SerializerProvider> mechanismus zjišťování.  Modul plug-in serializátorů nabízí rozšířené výhody pro snadné nasazení a používání celého systému.  Propojené serializátorů můžete implementovat také pro prostředí s částečnou důvěryhodností například [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] kde modulu plug-in serializátorů nejsou dostupné.  Propojené serializátorů, které jsou založeny na odvozené provádění <xref:System.Windows.Documents.Serialization.SerializerWriter> třídy, jsou kompilované a propojené přímo do aplikace.  Modul plug-in serializátorů a propojené serializátorů fungovat prostřednictvím identické veřejné metody a události, které usnadňují používat nebo oba typy serializátorů ve stejné aplikaci.  
  
 Modul plug-in serializátorů podpory vývojáři aplikace tím, že poskytuje rozšíření pro nové návrhy úložiště a formáty souborů bez nutnosti code přímo pro každý potenciální formátu v čase vytvoření buildu.  Modul plug-in serializátorů také těžit jiných společností tím, že poskytuje standardizovaná způsob, jak nasadit, nainstalovat a aktualizovat systém dostupné moduly plug-in pro vlastní nebo chráněných formátů.  
  
### <a name="using-a-plug-in-serializer"></a>Pomocí modulu Plug-in serializátor  
 Modul plug-in serializátorů jsou jednoduché na používání.  <xref:System.Windows.Documents.Serialization.SerializerProvider> Vytvoří výčet tříd <xref:System.Windows.Documents.Serialization.SerializerDescriptor> objekt pro každý modul plug-in nainstalované v systému.  <xref:System.Windows.Documents.Serialization.SerializerDescriptor.IsLoadable%2A> Vlastnost filtry nainstalované moduly plug-in na základě aktuální konfigurace a ověří, že serializátor můžete načíst a používá je aplikace.  <xref:System.Windows.Documents.Serialization.SerializerDescriptor> Poskytuje také další vlastnosti, jako <xref:System.Windows.Documents.Serialization.SerializerDescriptor.DisplayName%2A> a <xref:System.Windows.Documents.Serialization.SerializerDescriptor.DefaultFileExtension%2A>, které aplikace můžete použít pro vyzvání uživatele při výběru serializátoru pro k dispozici výstupní formát.  Výchozí modul plug-in serializátor pro [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] je součástí rozhraní .NET Framework a je vždycky vytvořit její výčet.  Poté, co uživatel vybere výstupní formát, <xref:System.Windows.Documents.Serialization.SerializerProvider.CreateSerializerWriter%2A> metoda se používá k vytvoření <xref:System.Windows.Documents.Serialization.SerializerWriter> pro konkrétní formát.  <xref:System.Windows.Documents.Serialization.SerializerWriter>.<xref:System.Windows.Documents.Serialization.SerializerWriter.Write%2A> pak nelze volat metodu do výstupního datového proudu dokumentu do úložiště dat.  
  
 Následující příklad ilustruje aplikaci, která používá <xref:System.Windows.Documents.Serialization.SerializerProvider> metoda ve vlastnosti "PlugInFileFilter".  PlugInFileFilter zobrazí nainstalované moduly plug-in a vytvoří řetězec filtru k dispozici soubor možnosti, jak <xref:Microsoft.Win32.SaveFileDialog>.  
  
 [!code-csharp[DocumentSerialize#DocSerializeFileFilter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DocumentSerialize/CSharp/ThumbViewer.cs#docserializefilefilter)]  
  
 Jakmile uživatel vybral název výstupního souboru, následující příklad ukazuje použití <xref:System.Windows.Documents.Serialization.SerializerProvider.CreateSerializerWriter%2A> metoda k uložení daného dokumentu v zadaném formátu.  
  
 [!code-csharp[DocumentSerialize#DocSerializePlugIn](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DocumentSerialize/CSharp/ThumbViewer.cs#docserializeplugin)]  
  
<a name="InstallingPluginSerializers"></a>   
### <a name="installing-plug-in-serializers"></a>Instalace modulu Plug-in Serializátorů  
 <xref:System.Windows.Documents.Serialization.SerializerProvider> Třída poskytuje vyšší úrovně aplikační rozhraní pro modul plug-in serializátor zjišťování a přístup.  <xref:System.Windows.Documents.Serialization.SerializerProvider> Vyhledá a poskytuje aplikace seznam serializátorů, které jsou nainstalované a dostupné v systému.  Specifikace nainstalované serializátorů jsou definovány prostřednictvím nastavení registru.  Modul plug-in serializátorů lze přidat do registru pomocí <xref:System.Windows.Documents.Serialization.SerializerProvider.RegisterSerializer%2A> metoda; nebo pokud rozhraní .NET Framework není ještě nainstalována, skript instalace modulu plug-in můžete přímo nastavit hodnoty registru sám sebe.  <xref:System.Windows.Documents.Serialization.SerializerProvider.UnregisterSerializer%2A> Metoda slouží k odebrání již nainstalovaného modul plug-in, nebo nastavení registru mohou být resetovat podobně skript, který odinstalaci.  
  
### <a name="creating-a-plug-in-serializer"></a>Vytváření modulu Plug-in serializátor  
 Modul plug-in serializátorů a serializátorů propojené pomocí stejné zveřejněné veřejné metody a události a stejně tak může být navržený pro použití synchronně nebo asynchronně.  Obvykle se používá k vytvoření serializátoru, modul plug-in tři základní kroky:  
  
1.  Implementace a ladění serializátor nejprve jako propojené serializátor.  Původně vytváření serializátor zkompilován a propojené přímo v testovací aplikaci poskytuje úplný přístup k zarážky a dalším službám ladění užitečné pro testování.  
  
2.  Po serializátor je plně otestovat, <xref:System.Windows.Documents.Serialization.ISerializerFactory> rozhraní přidá se modul plug-in.  <xref:System.Windows.Documents.Serialization.ISerializerFactory> Rozhraní umožňuje úplný přístup ke všem objektům rozhraní .NET Framework, což zahrnuje logického stromu <xref:System.Windows.UIElement> objekty, <xref:System.Windows.Documents.IDocumentPaginatorSource>, a <xref:System.Windows.Media.Visual> elementy.  Kromě <xref:System.Windows.Documents.Serialization.ISerializerFactory> poskytuje stejné synchronní a asynchronní metody a události používané propojené serializátorů.  Vzhledem k tomu, že velké dokumenty může trvat dobu výstup, asynchronních operací se doporučuje udržovat reagující uživatelské interakce a nabízet možnost tlačítko Storno"Pokud dojde k potížím s úložištěm dat.  
  
3.  Po vytvoření serializátoru, který je modul plug-in instalační skript je implementována pro distribuci a instalace (a odinstalace) modul plug-in (viz výše, "[instalace modulu Plug-in Serializátorů](#InstallingPluginSerializers)").  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Documents.Serialization>  
 <xref:System.Windows.Xps.XpsDocumentWriter>  
 <xref:System.Windows.Xps.Packaging.XpsDocument>  
 [Dokumenty v platformě WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Přehled tisku](../../../../docs/framework/wpf/advanced/printing-overview.md)  
 [XML Paper Specification: Přehled](http://go.microsoft.com/fwlink?LinkID=106246)
