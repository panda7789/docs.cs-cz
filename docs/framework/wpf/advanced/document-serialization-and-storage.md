---
title: Serializace a úložiště dokumentu
ms.date: 03/30/2017
helpviewer_keywords:
- 'serialization of documents [WPF], , '
- documents [WPF], storage
- documents [WPF], serialization
ms.assetid: 4839cd87-e206-4571-803f-0200098ad37b
ms.openlocfilehash: ff0555105f219db5ed891c02400b0587c825718e
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73974651"
---
# <a name="document-serialization-and-storage"></a>Serializace a úložiště dokumentu

Microsoft .NET Framework poskytuje výkonné prostředí pro vytváření a zobrazování vysoce kvalitních dokumentů.  Vylepšené funkce, které podporují rozšířené ovládací prvky pro práci s dokumenty a flow, jsou v kombinaci s výkonnými 2D a prostorovými grafickými možnostmi .NET Framework aplikací na novou úroveň kvality a uživatelského prostředí.  Schopnost pružně spravovat reprezentace dokumentu v paměti je klíčovou funkcí .NET Framework a může efektivně ukládat a načítat dokumenty z úložiště dat je potřeba skoro každou aplikaci.  Proces převodu dokumentu z interní reprezentace v paměti na externí úložiště dat je termínem serializace.  Zpětný proces čtení úložiště dat a opětovného vytvoření původní instance v paměti je označován jako deserializace.

<a name="AboutSerialization"></a>

## <a name="about-document-serialization"></a>O serializaci dokumentu

V ideálním případě proces serializace a deserializace dokumentu z a následně zpět do paměti je pro aplikaci transparentní.  Aplikace zavolá metodu serializátoru "Write" pro uložení dokumentu, zatímco metoda "čtení" pro deserializaci "přistupuje k úložišti dat a znovu vytvoří původní instanci v paměti.  Konkrétní formát, ve kterém jsou data uložena, většinou není obavou aplikace, pokud proces serializace a deserializace znovu vytvoří dokument zpět do původního formátu.

Aplikace často poskytují více možností serializace, které uživateli umožňují ukládat dokumenty na jiné médium nebo do jiného formátu.  Například aplikace může nabízet možnosti Uložit jako k uložení dokumentu na soubor na disku, databázi nebo webovou službu.  Podobně různé serializátory můžou dokument uložit v různých formátech, jako je HTML, RTF, XML, XPS, nebo alternativně k formátu třetí strany.  Do aplikace serializace definuje rozhraní, které izoluje podrobnosti o médiu úložiště v rámci implementace každého konkrétního serializátoru.  Kromě výhod zapouzdření podrobností úložiště poskytují rozhraní API pro .NET Framework <xref:System.Windows.Documents.Serialization> několik dalších důležitých funkcí.

### <a name="features-of-net-framework-30-document-serializers"></a>Funkce serializátorů dokumentů .NET Framework 3,0

- Přímý přístup k objektům vysoké úrovně (logický strom a vizuály) umožňuje efektivní ukládání stránkovaného obsahu, 2D/3D prvků, obrázků, médií, hypertextových odkazů, poznámek a dalšího obsahu podpory.

- Synchronní a asynchronní operace.

- Podpora pro serializátory modulů plug-in se zlepšenými možnostmi:

  - Přístup k celému systému pro použití všemi .NET Framework aplikacemi.

  - Zjistitelný modul plug-in aplikace Simple Application.

  - Jednoduché nasazení, instalace a aktualizace pro vlastní moduly plug-in třetích stran

  - Podpora uživatelského rozhraní pro vlastní nastavení a možnosti v době běhu.

### <a name="xps-print-path"></a>Cesta tisku XPS

Cesta pro tisk v Microsoft .NET Framework XPS také poskytuje rozšiřitelný mechanismus pro psaní dokumentů prostřednictvím výstupu tisku.  XPS slouží jako formát souboru dokumentu a je nativní formát pro zařazování tisku pro systém Windows Vista.  Dokumenty XPS je možné odesílat přímo do tiskáren kompatibilních s XPS bez nutnosti konverze do mezilehlého formátu.  Další informace o možnostech výstupu cesty tisku a možnostech najdete v tématu [Přehled tisku](printing-overview.md) .

<a name="PluginSerializers"></a>

## <a name="plug-in-serializers"></a>Serializátory modulů plug-in

Rozhraní API pro <xref:System.Windows.Documents.Serialization> poskytují podporu pro serializátory modulů plug-in i propojené serializátory, které jsou nainstalovány odděleně od aplikace, vážou v době běhu a jsou k dispozici pomocí mechanismu zjišťování <xref:System.Windows.Documents.Serialization.SerializerProvider>.  Modul pro serializace modulů plug-in nabízí lepší výhody pro snadné nasazení a použití v rámci systému.  Propojené serializátory lze také implementovat pro prostředí s částečným vztahem důvěryhodnosti, jako jsou například aplikace prohlížeče XAML (XBAP), kde nejsou k dispozici moduly pro serializace modulu plug-in.  Propojené serializátory, které jsou založeny na odvozené implementaci třídy <xref:System.Windows.Documents.Serialization.SerializerWriter>, jsou kompilovány a propojeny přímo do aplikace.  Moduly pro serializace a propojené serializátory pracují přes identické veřejné metody a události, které usnadňují použití buď nebo obou typů serializátorů ve stejné aplikaci.

Serializátory modulů plug-in pomáhají vývojářům aplikací poskytovat rozšiřitelnost novým návrhům úložiště a formátům souborů bez nutnosti kódu přímo pro každý potenciální formát v době sestavení.  Serializátory modulů plug-in také poskytují vývojářům třetích stran standardizované prostředky pro nasazení, instalaci a aktualizaci modulů plug-in pro přístup k systému pro vlastní nebo speciální formáty souborů.

### <a name="using-a-plug-in-serializer"></a>Použití serializátoru modulu plug-in

Moduly pro serializace modulu plug-in se snadno používají.  Třída <xref:System.Windows.Documents.Serialization.SerializerProvider> vytváří výčet <xref:System.Windows.Documents.Serialization.SerializerDescriptor>ch objektů pro každý modul plug-in nainstalovaný v systému.  Vlastnost <xref:System.Windows.Documents.Serialization.SerializerDescriptor.IsLoadable%2A> filtruje nainstalované moduly plug-in na základě aktuální konfigurace a ověřuje, že se serializátor dá načíst a používat v aplikaci.  <xref:System.Windows.Documents.Serialization.SerializerDescriptor> také poskytuje další vlastnosti, například <xref:System.Windows.Documents.Serialization.SerializerDescriptor.DisplayName%2A> a <xref:System.Windows.Documents.Serialization.SerializerDescriptor.DefaultFileExtension%2A>, které může aplikace použít k zobrazení výzvy uživateli při výběru serializátoru pro dostupný výstupní formát.  Výchozí modul plug-in pro XPS je k dispozici s .NET Framework a je vždy vyhodnocen.  Jakmile uživatel vybere výstupní formát, metoda <xref:System.Windows.Documents.Serialization.SerializerProvider.CreateSerializerWriter%2A> slouží k vytvoření <xref:System.Windows.Documents.Serialization.SerializerWriter> pro konkrétní formát.  Metodu <xref:System.Windows.Documents.Serialization.SerializerWriter.Write%2A?displayProperty=nameWithType> lze následně volat pro výstup datového proudu dokumentu do úložiště dat.

Následující příklad znázorňuje aplikaci, která používá metodu <xref:System.Windows.Documents.Serialization.SerializerProvider> ve vlastnosti "PlugInFileFilter".  PlugInFileFilter vytvoří výčet nainstalovaných modulů plug-in a sestaví řetězec filtru s dostupnými možnostmi souborů pro <xref:Microsoft.Win32.SaveFileDialog>.

[!code-csharp[DocumentSerialize#DocSerializeFileFilter](~/samples/snippets/csharp/VS_Snippets_Wpf/DocumentSerialize/CSharp/ThumbViewer.cs#docserializefilefilter)]

Jakmile uživatel vybere název výstupního souboru, následující příklad znázorňuje použití metody <xref:System.Windows.Documents.Serialization.SerializerProvider.CreateSerializerWriter%2A> k uložení daného dokumentu v zadaném formátu.

[!code-csharp[DocumentSerialize#DocSerializePlugIn](~/samples/snippets/csharp/VS_Snippets_Wpf/DocumentSerialize/CSharp/ThumbViewer.cs#docserializeplugin)]

<a name="InstallingPluginSerializers"></a>

### <a name="installing-plug-in-serializers"></a>Instalace serializátorů modulu plug-in

Třída <xref:System.Windows.Documents.Serialization.SerializerProvider> poskytuje rozhraní aplikace na nejvyšší úrovni pro zjišťování serializátorů a přístup k němu.  <xref:System.Windows.Documents.Serialization.SerializerProvider> vyhledá a poskytne aplikaci seznam serializátorů nainstalovaných a dostupných v systému.  Specifika instalovaných serializátorů je definována prostřednictvím nastavení registru.  Moduly plug-in serializátory lze do registru přidat pomocí metody <xref:System.Windows.Documents.Serialization.SerializerProvider.RegisterSerializer%2A>; nebo pokud .NET Framework ještě není nainstalovaná, instalační skript modulu plug-in může přímo nastavit samotné hodnoty registru.  Metodu <xref:System.Windows.Documents.Serialization.SerializerProvider.UnregisterSerializer%2A> lze použít k odebrání dříve nainstalovaného modulu plug-in nebo nastavení registru lze resetovat podobně pomocí skriptu pro odinstalování.

### <a name="creating-a-plug-in-serializer"></a>Vytvoření serializátoru modulu plug-in

Moduly pro serializace a propojené serializátory používají stejné exponované veřejné metody a události a podobně mohou být navrženy pro synchronní nebo asynchronní zpracování.  Pro vytvoření serializátoru modulu plug-in obvykle následuje tři základní kroky:

1. Implementujte a laďte nejprve serializátor jako propojený serializátor.  Počáteční vytvoření serializátoru zkompilovaného a připojeného přímo v testovací aplikaci poskytuje úplný přístup ke zarážekm a dalším službám ladění, které jsou užitečné pro testování.

2. Po úplném otestování serializátoru se přidá <xref:System.Windows.Documents.Serialization.ISerializerFactory> rozhraní, které vytvoří modul plug-in.  Rozhraní <xref:System.Windows.Documents.Serialization.ISerializerFactory> povoluje úplný přístup ke všem objektům .NET Framework, které zahrnují logický strom, <xref:System.Windows.UIElement> objektů, <xref:System.Windows.Documents.IDocumentPaginatorSource>a <xref:System.Windows.Media.Visual> prvků.  Navíc <xref:System.Windows.Documents.Serialization.ISerializerFactory> poskytuje stejné synchronní a asynchronní metody a události, které používají propojené serializátory.  Vzhledem k tomu, že velké dokumenty můžou nějakou dobu trvat, doporučujeme asynchronní operace, které udržují reagovat na uživatele a nabízejí možnost zrušit, pokud se v úložišti dat vyskytne nějaký problém.

3. Po vytvoření serializátoru modulu plug-in se instalační skript implementuje pro distribuci a instalaci (a odinstalaci) modulu plug-in (viz výše, "[instalace serializátorů modulu plug-in](#InstallingPluginSerializers)").

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Documents.Serialization>
- <xref:System.Windows.Xps.XpsDocumentWriter>
- <xref:System.Windows.Xps.Packaging.XpsDocument>
- [Dokumenty v platformě WPF](documents-in-wpf.md)
- [Přehled tisku](printing-overview.md)
- [Specifikace papíru XML: Přehled](https://go.microsoft.com/fwlink?LinkID=106246)
