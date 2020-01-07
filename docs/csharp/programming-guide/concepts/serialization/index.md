---
title: Serializace (C#)
ms.date: 01/02/2020
ms.openlocfilehash: 1d2bda9022b7e43744dd8a0286eff88914cf65a3
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635727"
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

Obor názvů <xref:System.Text.Json> obsahuje třídy pro serializaci a deserializaci JavaScript Object Notation (JSON). JSON je otevřený standard, který se běžně používá pro sdílení dat na celém webu.

Serializace JSON serializace veřejné vlastnosti objektu do řetězce, bajtového pole nebo datového proudu, který odpovídá [specifikaci JSON specifikace RFC 8259](https://tools.ietf.org/html/rfc8259). Chcete-li řídit způsob, jakým <xref:System.Text.Json.JsonSerializer> serializace nebo deserializace instance třídy:

* Použití objektu <xref:System.Text.Json.JsonSerializerOptions>
* Použití atributů z oboru názvů <xref:System.Text.Json.Serialization> na třídy nebo vlastnosti
* [Implementace vlastních převaděčů](../../../../standard/serialization/system-text-json-converters-how-to.md)

## <a name="binary-and-xml-serialization"></a>Binární a XML serializace

Obor názvů <xref:System.Runtime.Serialization> obsahuje třídy pro binární serializaci a serializaci XML a deserializaci.

Binární serializace používá binární kódování pro vytváření kompaktní serializace pro použití, jako je úložiště nebo síťové datové proudy založené na soketu. V binární serializaci jsou serializováni všichni členové, dokonce i členové, kteří jsou jen pro čtení, a výkon je vylepšen. 

Serializace XML serializace veřejné pole a vlastnosti objektu nebo parametry a návratové hodnoty metod do datového proudu XML, který odpovídá konkrétnímu dokumentu XSD (XML Schema Definition Language). Serializace XML má za následek třídy silného typu s veřejnými vlastnostmi a poli, které jsou převedeny na XML. <xref:System.Xml.Serialization> obsahuje třídy pro serializaci a deserializaci kódu XML. Můžete použít atributy na třídy a členy třídy pro řízení způsobu, jakým <xref:System.Xml.Serialization.XmlSerializer> serializace nebo deserializace instance třídy.

### <a name="making-an-object-serializable"></a>Vytvoření objektu, který je serializovatelný

Pro binární nebo XML serializaci budete potřebovat:

* Objekt, který se má serializovat
* Datový proud, který obsahuje serializovaný objekt
* Instance <xref:System.Runtime.Serialization.Formatter?displayProperty=fullName>

Použijte atribut <xref:System.SerializableAttribute> pro typ k označení toho, že instance typu mohou být serializovány. Pokud se pokusíte serializovat, ale typ nemá atribut <xref:System.SerializableAttribute>, je vyvolána výjimka.

Chcete-li zabránit serializaci pole, použijte atribut <xref:System.NonSerializedAttribute>. Pokud pole serializovatelný typ obsahuje ukazatel, popisovač nebo jinou strukturu dat, která je specifická pro konkrétní prostředí, a pole nemůže být smysluplně reustaveno v jiném prostředí, pak pravděpodobně budete chtít provést neserializaci.

Pokud serializovaná třída obsahuje odkazy na objekty jiných tříd, které jsou označeny <xref:System.SerializableAttribute>, budou tyto objekty také serializovány.

### <a name="basic-and-custom-serialization"></a>Základní a vlastní serializace

Binární a XML serializace lze provádět dvěma způsoby, Basic a Custom.

Základní serializace používá .NET Framework k automatickému serializaci objektu. Jediným požadavkem je, že třída má použit atribut <xref:System.SerializableAttribute>. <xref:System.NonSerializedAttribute> lze použít k udržení serializace konkrétních polí.

Když použijete základní serializaci, může vytváření verzí objektů způsobovat problémy. Pokud jsou důležité problémy se správou verzí, použijte vlastní serializaci. Základní serializace představuje nejjednodušší způsob, jak provést serializaci, ale neposkytuje velkou kontrolu nad procesem.

Ve vlastní serializaci můžete přesně určit, které objekty budou serializovány a jak budou provedeny. Třída musí být označena <xref:System.SerializableAttribute> a implementovat rozhraní <xref:System.Runtime.Serialization.ISerializable>. Pokud chcete, aby byl objekt reserializován vlastním způsobem, použijte vlastní konstruktor.

## <a name="designer-serialization"></a>Serializace návrháře

Serializace návrháře je speciální forma serializace, která zahrnuje druh trvalosti objektů přidružených k vývojářským nástrojům. Serializace návrháře je proces převodu objektu grafu na zdrojový soubor, který lze později použít k obnovení grafu objektu. Zdrojový soubor může obsahovat kód, značku nebo dokonce informace o tabulce SQL.

## <a name="BKMK_RelatedTopics"></a>Související témata a příklady  

[Přehled System. text. JSON](../../../../standard/serialization/system-text-json-overview.md) Ukazuje, jak získat knihovnu `System.Text.Json`.

[Postup serializace a deserializace JSON v rozhraní .NET](../../../../standard/serialization/system-text-json-how-to.md). Ukazuje, jak číst a zapisovat data objektů do a z JSON pomocí třídy <xref:System.Text.Json.JsonSerializer>.

[Návod: uchování objektu v aplikaci Visual Studio (C#)](walkthrough-persisting-an-object-in-visual-studio.md)  
Ukazuje, jak lze použít serializaci k uchování dat objektu mezi instancemi, což umožňuje ukládat hodnoty a načíst je při příštím vytvoření instance objektu.

[Čtení dat objektů ze souboru XML (C#)](how-to-read-object-data-from-an-xml-file.md)  
Ukazuje, jak číst data objektů, která byla dříve zapsána do souboru XML pomocí třídy <xref:System.Xml.Serialization.XmlSerializer>.

[Zápis dat objektů do souboru XML (C#)](how-to-write-object-data-to-an-xml-file.md)  
Ukazuje, jak napsat objekt z třídy do souboru XML pomocí třídy <xref:System.Xml.Serialization.XmlSerializer>.
