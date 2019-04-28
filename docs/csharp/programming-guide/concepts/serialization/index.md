---
title: Serializace (C#)
ms.date: 04/26/2018
ms.openlocfilehash: 638fdbd31912ffeb284d734e1f8ce2ecd879b540
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61680114"
---
# <a name="serialization-c"></a>Serializace (C#)

Serializace je proces převodu objektu do datového proudu bajtů k uložení objektu nebo přenést na paměti, databázi nebo souboru. Jejich hlavním účelem je pro uložení stavu objektu, aby bylo možné ho v případě potřeby znovu vytvořit. Reverzní proces se nazývá deserializace.

## <a name="how-serialization-works"></a>Principy serializace

Tento obrázek ukazuje celkový proces serializace:

![Obrázek serializace](./media/index/serialization-process.gif)

Je objekt serializován do datového proudu, který nese nejen data, ale informace o typu objektu, například jeho název verze, jazykovou verzi a sestavení. Z tohoto datového proudu mohou být uloženy v databázi, soubor nebo paměti.

### <a name="uses-for-serialization"></a>Možnosti použití serializace

Serializace umožňuje vývojářům uložit stav objektu a znovu ho podle potřeby, poskytují úložiště pro objekty, stejně jako data systému exchange. Prostřednictvím serializace, Vývojář můžete provádět akce, jako je odesílání objektu k vzdálené aplikaci prostřednictvím webové služby, předávání objektů z jedné domény, předávání objektů přes bránu firewall jako řetězec XML nebo zabezpečení nebo informace o uživateli napříč aplikacemi.

### <a name="making-an-object-serializable"></a>Umožnění serializace objektu

K serializaci objektu, je nutné objekt, který má být serializován, stream tak, aby obsahovala serializovaný objekt a s <xref:System.Runtime.Serialization.Formatter>. <xref:System.Runtime.Serialization> obsahuje třídy, které jsou potřebné pro serializaci a deserializaci objektů.

Použít <xref:System.SerializableAttribute> atribut typu k označení, že lze serializovat instance tohoto typu. Výjimka je vyvolána, pokud při pokusu o serializaci, ale typ nemá <xref:System.SerializableAttribute> atribut.

Pokud nechcete, aby pole v rámci vaší třídě může být serializovatelný, použije <xref:System.NonSerializedAttribute> atribut. Obsahuje-li pole serializovatelného typu ukazatel, popisovač nebo některé datová struktura, která je specifická pro konkrétní prostředí a pole nemůže být rekonstituován smysluplně v jiném prostředí, můžete chtít provést neserializovatelné.

Pokud serializovaná třídy obsahuje odkazy na objekty jiné třídy, které jsou označeny <xref:System.SerializableAttribute>, tyto objekty se také serializovat.

## <a name="binary-and-xml-serialization"></a>Binární mapování a serializace XML

Můžete použít nebo binární serializace XML. Binární serializace, všichni členové serializují dokonce členové, které jsou jen pro čtení, a výkon je zvýšen. Serializace XML obsahuje kód lépe čitelný a větší pružnost využití pro zajištění spolupráce a sdílení objektu.

### <a name="binary-serialization"></a>Binární serializace

Binární serializace používá k vytvoření compact serializace pro použití jako úložiště nebo síťové sokety datové proudy binární kódování.

### <a name="xml-serialization"></a>serializace XML

Serializace XML serializuje veřejné polí a vlastností objektu, nebo parametry a návratovými hodnotami metod do datový proud XML, který odpovídá určitého dokumentu schématu XML definice jazyk (XSD). Výsledky serializace XML v silného typu třídy s veřejné vlastnosti a pole, které jsou převedeny na XML. <xref:System.Xml.Serialization> obsahuje třídy, které jsou potřebné pro serializaci a deserializaci XML.

Použití atributů na třídy a třídy členy lze řídit způsob, jakým <xref:System.Xml.Serialization.XmlSerializer> serializuje a deserializuje instance třídy.

## <a name="basic-and-custom-serialization"></a>Základní a vlastní serializace

Serializace lze provést dvěma způsoby, základní a vlastní. Základní serializace rozhraní .NET Framework používá k serializaci objektu automaticky.

### <a name="basic-serialization"></a>Základní serializace

Jediným požadavkem v základní serializace je, že objekt má <xref:System.SerializableAttribute> atribut. <xref:System.NonSerializedAttribute> Je možné zabránit serializována konkrétních polí.

Pokud používáte základní serializace, Správa verzí objektů může způsobovat problémy. Vlastní serializace byste použili, když jsou důležité, Správa verzí – potíže. Základní serializace je nejjednodušší způsob, jak provést serializace, ale neposkytuje velkou kontrolu nad tímto procesem.

### <a name="custom-serialization"></a>Vlastní serializace

Ve vlastní serializace je zadat přesně objektů, které bude serializována a jak provést. Musí být třída označena <xref:System.SerializableAttribute> a implementovat <xref:System.Runtime.Serialization.ISerializable> rozhraní.

Pokud chcete, aby váš objekt mohl deserializovat vlastní způsobem, je nutné použít vlastního konstruktoru.

## <a name="designer-serialization"></a>Serializace návrháře

Serializace návrháře je zvláštní forma serializace, která zahrnuje druh objektu trvalost spojené s vývojovými nástroji. Návrháře serializace je proces převodu grafu objektu do zdrojového souboru, který lze později obnovit grafu objektů. Zdrojový soubor může obsahovat kód, značek nebo dokonce i informace o tabulce SQL.

## <a name="BKMK_RelatedTopics"></a> Související témata a příklady  
[Návod: Uchování objektu v sadě Visual Studio (C#)](walkthrough-persisting-an-object-in-visual-studio.md)  
Ukazuje, jak serializace může být použita k uchování dat objektu mezi instancemi, umožňuje uložení hodnot a načíst je dalším je vytvořena instance objektu.

[Postupy: Čtení dat objektů ze souboru XML (C#)](how-to-read-object-data-from-an-xml-file.md)  
 Znázorňuje způsob čtení dat objektů, které se předtím zapsala do souboru XML pomocí <xref:System.Xml.Serialization.XmlSerializer> třídy.

[Postupy: Zápis dat objektů do souboru XML (C#)](how-to-write-object-data-to-an-xml-file.md)  
Ukazuje, jak zapsat objekt ze třídy do souboru XML pomocí <xref:System.Xml.Serialization.XmlSerializer> třídy.
