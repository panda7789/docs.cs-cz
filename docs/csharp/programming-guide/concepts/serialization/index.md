---
title: Serializace (C#)
ms.date: 04/26/2018
ms.openlocfilehash: 03a7cd2d48b79d94674e64e96130e20a86051fb2
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/10/2018
ms.locfileid: "33957850"
---
# <a name="serialization-c"></a>Serializace (C#)

Serializace je proces převodu objektu do datového proudu bajtů pro ukládání objektu nebo na přenos do paměti, databáze nebo souboru. Jeho hlavním účelem je pro uložení stavu objektu, aby bylo možné ho v případě potřeby znovu vytvořit. Zpětné proces se nazývá deserializace.

## <a name="how-serialization-works"></a>Jak funguje serializace

Tento obrázek ukazuje celý proces serializace.

![Obrázek serializace](./media/serialization.gif "serializace")

Je objekt serializován do datového proudu, který nese nejen data, ale informace o typu objektu, například jeho název verze, jazykovou verzi a sestavení. Z tohoto datového proudu mohou být uloženy do databáze, soubor nebo paměti.

### <a name="uses-for-serialization"></a>Používá pro serializaci

Serializace umožňuje vývojáři ho znovu vytvořit podle potřeby, poskytuje úložiště objektů, jakož i výměny dat a uložit stav objektu. Prostřednictvím serializace, vývojáři mohou provádět akce jako odesílání objektu do vzdálené aplikace prostřednictvím webové služby, předávání objektů z jedné domény na jiný, předávání objektů přes bránu firewall jako řetězec v kódu XML nebo zachování zabezpečení nebo informace o uživateli ve všech aplikacích.

### <a name="making-an-object-serializable"></a>Změna objektu serializovatelný

O serializaci objektu, je nutné objekt, který má být serializován datového proudu tak, aby obsahovala serializovaný objekt a <xref:System.Runtime.Serialization.Formatter>. <xref:System.Runtime.Serialization> obsahuje třídy, které jsou nezbytné pro serializaci a deserializaci objektů.

Použít <xref:System.SerializableAttribute> atribut typ indikující, že instance tohoto typu lze serializovat. Pokud se pokusíte k serializaci, ale nemá typ je vyvolána výjimka <xref:System.SerializableAttribute> atribut.

Pokud nechcete, aby pole v rámci vaší třídy být serializovatelný, budou použity <xref:System.NonSerializedAttribute> atribut. Pokud pole typu serializable obsahuje ukazatel, popisovač nebo některé další datová struktura, která je specifická pro konkrétní prostředí a pole nemůže být obnoveny srozumitelně v jiném prostředí, můžete chtít provést neserializovatelné.

Pokud serializovaných třída obsahuje odkazy na objekty jiné třídy, které jsou označené <xref:System.SerializableAttribute>, ty objekty, budou také serializována.

## <a name="binary-and-xml-serialization"></a>Binární a serializace XML

Můžete použít nebo binární serializace XML. V binární serializace, všichni členové se serializují i členů, které jsou jen pro čtení, a je lepší výkon. Serializace XML poskytuje srozumitelnější kód a větší flexibilitu objekt sdílení a využití pro zajištění spolupráce.

### <a name="binary-serialization"></a>Binární serializace

Binární serializace používá k vytvoření compact serializace pro účely třeba úložiště nebo sítě založené na soket datové proudy binárního kódování.

### <a name="xml-serialization"></a>serializace XML

Serializace XML serializuje veřejná pole a vlastnosti objektu, nebo parametry a návratové hodnoty metod, do datový proud XML, který odpovídá konkrétní jazyk (XSD) dokumentu definice schématu XML. Výsledky serializace XML v silného typu třídy s veřejné vlastnosti a pole, které jsou převedeny na XML. <xref:System.Xml.Serialization> obsahuje třídy, které jsou nezbytné pro serializaci a deserializaci XML.

Použití atributů pro třídy a jejich členové k řízení způsobu <xref:System.Xml.Serialization.XmlSerializer> serializuje a deserializuje instance třídy.

## <a name="basic-and-custom-serialization"></a>Základní a vlastní serializace

Serializace lze provést dvěma způsoby, základní a vlastní. Základní serializace používá k serializaci objektu automaticky rozhraní .NET Framework.

### <a name="basic-serialization"></a>Základní serializace

Jediným požadavkem v základní serializace je, že objekt obsahuje <xref:System.SerializableAttribute> atribut použitý. <xref:System.NonSerializedAttribute> Lze použít k udržování konkrétních polí z serializována.

Pokud používáte základní serializace, Správa verzí objektů může způsobit problémy. Vlastní serializace byste použili v případě problémů jsou důležité. Základní serializace je nejjednodušší způsob, jak provést serializaci, ale neposkytuje mnohem kontrolu nad tímto procesem.

### <a name="custom-serialization"></a>Vlastní serializace

V vlastní serializace můžete zadat přesně objektů, které budou serializovány a jak bude provedeno. Třída musí být označen <xref:System.SerializableAttribute> a implementovat <xref:System.Runtime.Serialization.ISerializable> rozhraní.

Pokud chcete objektu k deserializaci vlastní způsobem, musíte použít vlastní konstruktor.

## <a name="designer-serialization"></a>Návrhář serializace

Návrhář serializace je speciální forma serializace, který zahrnuje druh objektu trvalost přidružené nástroje pro vývoj. Návrhář serializace je proces převodu grafu objektu zdrojového souboru, který můžete později použít k obnovení grafu objektu. Zdrojový soubor může obsahovat kód, značka nebo i informace o tabulce SQL.

##  <a name="BKMK_RelatedTopics"></a> Příklady a související témata  
[Návod: Uchování objektu v sadě Visual Studio (C#)](walkthrough-persisting-an-object-in-visual-studio.md)  
Ukazuje, jak serializace může být použita k uchování dat objektu mezi instancemi, který vám umožní ukládat hodnoty a je načtou při příštím vytvoření instance objektu.

[Postupy: čtení dat objektů ze souboru XML (C#)](how-to-read-object-data-from-an-xml-file.md)  
 Ukazuje, jak číst data objektu, která byla dříve zapsána do souboru XML pomocí <xref:System.Xml.Serialization.XmlSerializer> třídy.

[Postupy: zápis dat objektů do souboru XML (C#)](how-to-write-object-data-to-an-xml-file.md)  
Ukazuje, jak k zápisu objektu od třídy, do souboru XML pomocí <xref:System.Xml.Serialization.XmlSerializer> třídy.
