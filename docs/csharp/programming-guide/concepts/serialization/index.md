---
title: Serializace (C#)
ms.date: 01/02/2020
ms.openlocfilehash: d914298a370b09307e84c88959542b4823cf37ce
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79167592"
---
# <a name="serialization-c"></a>Serializace (C#)

Serializace je proces převodu objektu do datového proudu bajtů pro uložení objektu nebo jeho přenos do paměti, databáze nebo souboru. Jeho hlavním účelem je uložit stav objektu, aby bylo možné jej znovu vytvořit v případě potřeby. Opačný proces se nazývá deserializace.

## <a name="how-serialization-works"></a>Jak serializace funguje

Tento obrázek znázorňuje celkový proces serializace:

![Obrázek serializace](./media/index/serialization-process.gif)

Objekt je serializován do datového proudu, který nese data. Datový proud může mít také informace o typu objektu, jako je jeho verze, jazyková verze a název sestavení. Z tohoto datového proudu může být objekt uložen v databázi, souboru nebo paměti.

### <a name="uses-for-serialization"></a>Použití pro serializaci

Serializace umožňuje vývojáři uložit stav objektu a znovu jej vytvořit podle potřeby, poskytuje ukládání objektů, stejně jako výměnu dat. Prostřednictvím serializace může vývojář provádět akce, jako jsou:

* Odeslání objektu do vzdálené aplikace pomocí webové služby
* Předání objektu z jedné domény do jiné
* Předání objektu bránou firewall jako řetězec JSON nebo XML
* Udržování informací o zabezpečení nebo specifických informací o uživateli v různých aplikacích

## <a name="json-serialization"></a>Serializace JSON

Obor <xref:System.Text.Json> názvů obsahuje třídy pro serializaci a deserializaci javascriptového zápisu objektu (JSON). JSON je otevřený standard, který se běžně používá pro sdílení dat na webu.

Serializace JSON serializuje veřejné vlastnosti objektu do řetězce, bajtového pole nebo datového proudu, který odpovídá [specifikaci RFC 8259 JSON](https://tools.ietf.org/html/rfc8259). Chcete-li <xref:System.Text.Json.JsonSerializer> řídit způsob serializace nebo rekonstrukci instance třídy:

* Použití <xref:System.Text.Json.JsonSerializerOptions> objektu
* Použití atributů <xref:System.Text.Json.Serialization> z oboru názvů na třídy nebo vlastnosti
* [Implementace vlastních převaděčů](../../../../standard/serialization/system-text-json-converters-how-to.md)

## <a name="binary-and-xml-serialization"></a>Binární a XML serializace

Obor <xref:System.Runtime.Serialization> názvů obsahuje třídy pro binární a XML serializaci a deserializaci.

Binární serializace používá binární kódování k vytvoření kompaktní serializace pro použití, jako jsou síťové proudy založené na úložišti nebo soketu. V binární serializace jsou všechny členy, i členy, které jsou jen pro čtení, serializovány a výkon je zvýšen.

Serializace XML serializuje veřejná pole a vlastnosti objektu nebo parametry a vrácené hodnoty metod do datového proudu XML, který odpovídá dokumentu jazyka XSD specifického jazyka XML Schema. Výsledkem serializace XML jsou třídy silného typu s veřejnými vlastnostmi a poli, které jsou převedeny na XML. <xref:System.Xml.Serialization>obsahuje třídy pro serializaci a deserializaci XML. Atributy použijete na třídy a členy <xref:System.Xml.Serialization.XmlSerializer> třídy k řízení způsobu serializace nebo deserializace instance třídy.

### <a name="making-an-object-serializable"></a>Serializovatelný objekt

Pro binární nebo XML serializaci potřebujete:

* Objekt, který má být serializován
* Datový proud obsahující serializovaný objekt
* Instance <xref:System.Runtime.Serialization.Formatter?displayProperty=fullName>

Použijte <xref:System.SerializableAttribute> atribut typu k označení, že instance typu lze serializovat. Výjimka je vyvolána, pokud se pokusíte serializovat, <xref:System.SerializableAttribute> ale typ nemá atribut.

Chcete-li zabránit serializování pole, použijte <xref:System.NonSerializedAttribute> atribut. Pokud pole serializovatelného typu obsahuje ukazatel, popisovač nebo jinou datovou strukturu, která je specifická pro určité prostředí, a pole nelze smysluplně rekonstituovat v jiném prostředí, můžete jej provést jako neserializovatelné.

Pokud serializovaná třída obsahuje odkazy na objekty <xref:System.SerializableAttribute>jiných tříd, které jsou označeny , budou tyto objekty také serializovány.

### <a name="basic-and-custom-serialization"></a>Základní a vlastní serializace

Binární a XML serializace může být provedena dvěma způsoby, základní a vlastní.

Základní serializace používá rozhraní .NET Framework k automatické serializaci objektu. Jediným požadavkem je, <xref:System.SerializableAttribute> že třída má atribut použít. Lze <xref:System.NonSerializedAttribute> zabránit serializovat konkrétní pole.

Při použití základní serializace může správa verzí objektů způsobit problémy. Vlastní serializaci byste použili, pokud jsou důležité problémy se správu verzí. Základní serializace je nejjednodušší způsob, jak provést serializaci, ale neposkytuje velkou kontrolu nad procesem.

Ve vlastní serializaci můžete přesně určit, které objekty budou serializovány a jak se to bude provádět. Třída musí být <xref:System.SerializableAttribute> označena <xref:System.Runtime.Serialization.ISerializable> a implementovat rozhraní. Pokud chcete, aby byl objekt rekonstruován také vlastním způsobem, použijte vlastní konstruktor.

## <a name="designer-serialization"></a>Serializace návrháře

Serializace návrháře je speciální forma serializace, která zahrnuje druh trvalost objektu spojené s vývojovými nástroji. Serializace návrháře je proces převodu objektového grafu na zdrojový soubor, který lze později použít k obnovení grafu objektů. Zdrojový soubor může obsahovat informace o kódu, značkách nebo dokonce tabulce SQL.

## <a name="BKMK_RelatedTopics"></a>Příbuzná témata a příklady  

[System.Text.Json - přehled](../../../../standard/serialization/system-text-json-overview.md) Ukazuje, jak `System.Text.Json` získat knihovnu.

[Serializace a deserializace zařízení JSON v rozhraní .NET](../../../../standard/serialization/system-text-json-how-to.md).
Ukazuje, jak číst a zapisovat data <xref:System.Text.Json.JsonSerializer> objektů do a z JSON pomocí třídy.

[Návod: Trvalé vytvoření objektu v sadě Visual Studio (C#)](walkthrough-persisting-an-object-in-visual-studio.md)  
Ukazuje, jak serializace lze použít k uchování dat objektu mezi instancemi, což umožňuje ukládat hodnoty a načíst je při příštím vytvoření instance objektu.

[Čtení dat objektu ze souboru XML (C#)](how-to-read-object-data-from-an-xml-file.md)  
Ukazuje, jak číst data o objektech, která <xref:System.Xml.Serialization.XmlSerializer> byla dříve zapsána do souboru XML pomocí třídy.

[Jak zapisovat data objektů do souboru XML (C#)](how-to-write-object-data-to-an-xml-file.md)  
Ukazuje, jak zapsat objekt z třídy <xref:System.Xml.Serialization.XmlSerializer> do souboru XML pomocí třídy.
