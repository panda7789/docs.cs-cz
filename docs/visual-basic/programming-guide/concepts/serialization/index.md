---
title: Serializace
ms.date: 07/20/2015
ms.assetid: 67379a76-5465-4af8-a781-0b0b25a62d9a
ms.openlocfilehash: 9ce97e541cb204b92663464e36d9e8f221ccc3f2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351917"
---
# <a name="serialization-visual-basic"></a>Serializace (Visual Basic)
Serializace je proces převodu objektu na proud bajtů za účelem uložení objektu nebo jeho odeslání do paměti, databáze nebo souboru. Hlavním účelem je uložit stav objektu, aby bylo možné ho v případě potřeby znovu vytvořit. Reverzní proces se nazývá deserializace.  
  
## <a name="how-serialization-works"></a>Principy serializace  
 Tento obrázek ukazuje celkový proces serializace.  
  
![Grafika serializace](./media/index/serialization-process.gif)
  
 Objekt je serializován do datového proudu, který nestačí pouze data, ale informace o typu objektu, jako je jeho verze, jazyková verze a název sestavení. Z tohoto datového proudu je možné ho uložit do databáze, souboru nebo paměti.  
  
### <a name="uses-for-serialization"></a>Možnosti použití serializace  
 Serializace umožňuje vývojářům uložit stav objektu a znovu ho vytvořit, a to tak, že poskytuje úložiště objektů i výměnu dat. Prostřednictvím serializace může vývojář provádět akce, jako je odeslání objektu do vzdálené aplikace, prostřednictvím webové služby, předání objektu z jedné domény do druhé, předání objektu přes bránu firewall jako řetězce XML nebo udržování zabezpečení nebo informace specifické pro uživatele napříč aplikacemi.  
  
### <a name="making-an-object-serializable"></a>Umožnění serializace objektu  
 Pro serializaci objektu potřebujete objekt k serializaci, datový proud, který bude obsahovat serializovaný objekt, a <xref:System.Runtime.Serialization.Formatter>. <xref:System.Runtime.Serialization> obsahuje třídy, které jsou nezbytné pro serializaci a deserializaci objektů.  
  
 Použijte atribut <xref:System.SerializableAttribute> pro typ k označení toho, že instance tohoto typu mohou být serializovány. Pokud se pokusíte serializovat, ale typ nemá atribut <xref:System.SerializableAttribute>, je vyvolána výjimka <xref:System.Runtime.Serialization.SerializationException>.  
  
 Pokud nechcete, aby bylo pole v rámci vaší třídy serializovatelný, použijte atribut <xref:System.NonSerializedAttribute>. Pokud pole serializovatelný typ obsahuje ukazatel, popisovač nebo jinou strukturu dat, která je specifická pro konkrétní prostředí, a pole nemůže být smysluplně reustaveno v jiném prostředí, pak pravděpodobně budete chtít provést neserializaci.  
  
 Pokud serializovaná třída obsahuje odkazy na objekty jiných tříd, které jsou označeny <xref:System.SerializableAttribute>, budou tyto objekty také serializovány.  
  
## <a name="binary-and-xml-serialization"></a>Binární serializace a serializace XML  
 Lze použít binární nebo XML serializaci. V binární serializaci jsou serializovány všechny členy, i ty, které jsou jen pro čtení, a zvyšují výkon. Serializace XML poskytuje čitelnější kód a také větší flexibilitu sdílení objektů a využití pro účely interoperability.  
  
### <a name="binary-serialization"></a>Binární serializace  
 Binární serializace používá binární kódování pro vytváření kompaktní serializace pro použití, jako je úložiště nebo síťové datové proudy založené na soketu.  
  
### <a name="xml-serialization"></a>Serializace XML  
 Serializace XML serializace veřejné pole a vlastnosti objektu nebo parametry a návratové hodnoty metod do datového proudu XML, který odpovídá konkrétnímu dokumentu XSD (XML Schema Definition Language). Serializace XML má za následek třídy silného typu s veřejnými vlastnostmi a poli, které jsou převedeny na XML. <xref:System.Xml.Serialization> obsahuje třídy potřebné pro serializaci a deserializaci kódu XML.  
  
 Můžete použít atributy na třídy a členy třídy, aby bylo možné řídit způsob, jakým <xref:System.Xml.Serialization.XmlSerializer> serializace nebo deserializace instance třídy.  
  
## <a name="basic-and-custom-serialization"></a>Základní a vlastní serializace  
 Serializaci lze provádět dvěma způsoby, Basic a Custom. Základní serializace používá .NET Framework k automatickému serializaci objektu.  
  
### <a name="basic-serialization"></a>Základní serializace  
 Jediným požadavkem při serializaci Basic je, že objekt má použit atribut <xref:System.SerializableAttribute>. <xref:System.NonSerializedAttribute> lze použít k udržení serializace konkrétních polí.  
  
 Při použití základní serializace mohou verze objektů vytvářet problémy, v takovém případě může být vhodnější vlastní serializace. Základní serializace představuje nejjednodušší způsob, jak provést serializaci, ale neposkytuje velkou kontrolu nad procesem.  
  
### <a name="custom-serialization"></a>Vlastní serializace  
 Ve vlastní serializaci můžete přesně určit, které objekty budou serializovány a jak budou provedeny. Třída musí být označena <xref:System.SerializableAttribute> a implementovat rozhraní <xref:System.Runtime.Serialization.ISerializable>.  
  
 Pokud chcete, aby byl objekt rekonstruován vlastním způsobem, je nutné použít vlastní konstruktor.  
  
## <a name="designer-serialization"></a>Serializace s použitím návrháře  
 Serializace návrháře je speciální forma serializace, která zahrnuje druh trvalosti objektu, který je obvykle přidružen k vývojářským nástrojům. Serializace návrháře je proces převodu objektu grafu na zdrojový soubor, který lze později použít k obnovení grafu objektu. Zdrojový soubor může obsahovat kód, značku nebo dokonce informace o tabulce SQL.  
  
## <a name="BKMK_RelatedTopics"></a>Související témata a příklady  
 [Návod: uchování objektu v aplikaci Visual Studio (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/walkthrough-persisting-an-object-in-visual-studio.md)  
 Ukazuje, jak lze použít serializaci k uchování dat objektu mezi instancemi, což umožňuje ukládat hodnoty a načíst je při příštím vytvoření instance objektu.  
  
 [Postupy: čtení dat objektů ze souboru XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)  
 Ukazuje, jak číst data objektů, která byla dříve zapsána do souboru XML pomocí třídy <xref:System.Xml.Serialization.XmlSerializer>.  
  
 [Postupy: zápis dat objektů do souboru XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)  
 Ukazuje, jak napsat objekt z třídy do souboru XML pomocí třídy <xref:System.Xml.Serialization.XmlSerializer>.
