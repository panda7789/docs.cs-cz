---
title: Serializace (C#)
ms.date: 01/02/2020
ms.openlocfilehash: b2532ccf281fdfaa951d56675066f1e239f9f480
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241978"
---
# <a name="serialization-c"></a>Serializace (C#)

Serializace je proces převodu objektu na datový proud bajtů pro uložení objektu nebo jeho odeslání do paměti, databáze nebo souboru. Hlavním účelem je uložit stav objektu, aby bylo možné ho v případě potřeby znovu vytvořit. Reverzní proces se nazývá deserializace.

## <a name="how-serialization-works"></a>Princip serializace

Tento obrázek ukazuje celkový proces serializace:

![Grafika serializace](./media/index/serialization-process.gif)

Objekt je serializován do datového proudu, který data přenáší. Datový proud může obsahovat také informace o typu objektu, jako je jeho verze, jazyková verze a název sestavení. Z tohoto datového proudu může být objekt uložen v databázi, souboru nebo paměti.

### <a name="uses-for-serialization"></a>Použití pro serializaci

Serializace umožňuje vývojářům uložit stav objektu a v případě potřeby ho vytvořit znovu, což poskytuje úložiště objektů i výměnu dat. Pomocí serializace může vývojář provádět následující akce:

* Odeslání objektu do vzdálené aplikace pomocí webové služby
* Předání objektu z jedné domény do druhé
* Předání objektu přes bránu firewall jako řetězce JSON nebo XML
* Údržba informací o zabezpečení nebo specifických pro uživatele napříč aplikacemi

## <a name="json-serialization"></a>Serializace JSON

<xref:System.Text.Json>Obor názvů obsahuje třídy pro serializaci a deserializaci JavaScript Object Notation (JSON). JSON je otevřený standard, který se běžně používá pro sdílení dat na celém webu.

Serializace JSON serializace veřejné vlastnosti objektu do řetězce, bajtového pole nebo datového proudu, který odpovídá [specifikaci JSON specifikace RFC 8259](https://tools.ietf.org/html/rfc8259). Chcete-li řídit způsob, jakým <xref:System.Text.Json.JsonSerializer> serializace nebo deserializace instance třídy:

* Použití <xref:System.Text.Json.JsonSerializerOptions> objektu
* Použití atributů z <xref:System.Text.Json.Serialization> oboru názvů na třídy nebo vlastnosti
* [Implementace vlastních převaděčů](../../../../standard/serialization/system-text-json-converters-how-to.md)

## <a name="binary-and-xml-serialization"></a>Binární a XML serializace

<xref:System.Runtime.Serialization>Obor názvů obsahuje třídy pro binární a serializaci a deserializaci kódu XML.

Binární serializace používá binární kódování pro vytváření kompaktní serializace pro použití, jako je úložiště nebo síťové datové proudy založené na soketu. V binární serializaci jsou serializováni všichni členové, dokonce i členové, kteří jsou jen pro čtení, a výkon je vylepšen.

Serializace XML serializace veřejné pole a vlastnosti objektu nebo parametry a návratové hodnoty metod do datového proudu XML, který odpovídá konkrétnímu dokumentu XSD (XML Schema Definition Language). Serializace XML má za následek třídy silného typu s veřejnými vlastnostmi a poli, které jsou převedeny na XML. <xref:System.Xml.Serialization>obsahuje třídy pro serializaci a deserializaci kódu XML. Můžete použít atributy na třídy a členy třídy pro řízení způsobu, jakým <xref:System.Xml.Serialization.XmlSerializer> serializace nebo deserializace instance třídy.

### <a name="making-an-object-serializable"></a>Vytvoření objektu, který je serializovatelný

Pro binární nebo XML serializaci budete potřebovat:

* Objekt, který se má serializovat
* Datový proud, který obsahuje serializovaný objekt
* <xref:System.Runtime.Serialization.Formatter?displayProperty=fullName>Instance

Použijte <xref:System.SerializableAttribute> atribut na typ, který označuje, že instance typu mohou být serializovány. Pokud se pokusíte serializovat, ale typ nemá atribut, je vyvolána výjimka <xref:System.SerializableAttribute> .

Chcete-li zabránit serializaci pole, použijte <xref:System.NonSerializedAttribute> atribut. Pokud pole serializovatelný typ obsahuje ukazatel, popisovač nebo jinou strukturu dat, která je specifická pro konkrétní prostředí, a pole nemůže být smysluplně reustaveno v jiném prostředí, pak pravděpodobně budete chtít provést neserializaci.

Obsahuje-li serializovaná třída odkazy na objekty jiných tříd, které jsou označeny <xref:System.SerializableAttribute> , budou tyto objekty také serializovány.

### <a name="basic-and-custom-serialization"></a>Základní a vlastní serializace

Binární a XML serializace lze provádět dvěma způsoby, Basic a Custom.

Základní serializace používá rozhraní .NET k automatické serializaci objektu. Jediným požadavkem je, že třída má <xref:System.SerializableAttribute> atribut použit. <xref:System.NonSerializedAttribute>Lze použít k udržení serializace konkrétních polí.

Když použijete základní serializaci, může vytváření verzí objektů způsobovat problémy. Pokud jsou důležité problémy se správou verzí, použijte vlastní serializaci. Základní serializace představuje nejjednodušší způsob, jak provést serializaci, ale neposkytuje velkou kontrolu nad procesem.

Ve vlastní serializaci můžete přesně určit, které objekty budou serializovány a jak budou provedeny. Třída musí být označena <xref:System.SerializableAttribute> a implementovat <xref:System.Runtime.Serialization.ISerializable> rozhraní. Pokud chcete, aby byl objekt reserializován vlastním způsobem, použijte vlastní konstruktor.

## <a name="designer-serialization"></a>Serializace návrháře

Serializace návrháře je speciální forma serializace, která zahrnuje druh trvalosti objektů přidružených k vývojářským nástrojům. Serializace návrháře je proces převodu objektu grafu na zdrojový soubor, který lze později použít k obnovení grafu objektu. Zdrojový soubor může obsahovat kód, značku nebo dokonce informace o tabulce SQL.

## <a name="related-topics-and-examples"></a><a name="BKMK_RelatedTopics"></a>Související témata a příklady  

[Přehled System. text. JSON](../../../../standard/serialization/system-text-json-overview.md) Ukazuje, jak získat `System.Text.Json` knihovnu.

[Postup serializace a deserializace JSON v rozhraní .NET](../../../../standard/serialization/system-text-json-how-to.md).
Ukazuje, jak číst a zapisovat data objektů do a z JSON pomocí <xref:System.Text.Json.JsonSerializer> třídy.

[Návod: uchování objektu v aplikaci Visual Studio (C#)](walkthrough-persisting-an-object-in-visual-studio.md)  
Ukazuje, jak lze použít serializaci k uchování dat objektu mezi instancemi, což umožňuje ukládat hodnoty a načíst je při příštím vytvoření instance objektu.

[Čtení dat objektů ze souboru XML (C#)](how-to-read-object-data-from-an-xml-file.md)  
Ukazuje, jak číst data objektů, která byla dříve zapsána do souboru XML pomocí <xref:System.Xml.Serialization.XmlSerializer> třídy.

[Zápis dat objektů do souboru XML (C#)](how-to-write-object-data-to-an-xml-file.md)  
Ukazuje, jak napsat objekt z třídy do souboru XML pomocí <xref:System.Xml.Serialization.XmlSerializer> třídy.
