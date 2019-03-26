---
title: Serializace (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 67379a76-5465-4af8-a781-0b0b25a62d9a
---
# <a name="serialization-visual-basic"></a>Serializace (Visual Basic)
Serializace je proces převodu objektu do datového proudu bajtů za účelem uložení objektu nebo přenášet do paměti, databázi nebo souboru. Jejich hlavním účelem je pro uložení stavu objektu, aby bylo možné ho v případě potřeby znovu vytvořit. Reverzní proces se nazývá deserializace.  
  
## <a name="how-serialization-works"></a>Principy serializace  
 Tento obrázek ukazuje celkový proces serializace.  
  
![Obrázek serializace](./media/index/serialization-process.gif)
  
 Je objekt serializován do datového proudu, který nese nejen data, ale informace o typu objektu, například jeho název verze, jazykovou verzi a sestavení. Z tohoto datového proudu mohou být uloženy v databázi, soubor nebo paměti.  
  
### <a name="uses-for-serialization"></a>Možnosti použití serializace  
 Serializace umožňuje vývojářům uložit stav objektu a znovu ho podle potřeby, poskytují úložiště pro objekty, stejně jako data systému exchange. Prostřednictvím serializace, Vývojář můžete provádět akce, jako je odesílání objektu k vzdálené aplikaci prostřednictvím webové služby, předávání objektů z jedné domény, předávání objektů přes bránu firewall jako řetězec XML nebo zabezpečení nebo informace o uživateli napříč aplikacemi.  
  
### <a name="making-an-object-serializable"></a>Umožnění serializace objektu  
 K serializaci objektu, je nutné objekt, který má být serializován, stream tak, aby obsahovala serializovaný objekt a s <xref:System.Runtime.Serialization.Formatter>. <xref:System.Runtime.Serialization> obsahuje třídy, které jsou potřebné pro serializaci a deserializaci objektů.  
  
 Použít <xref:System.SerializableAttribute> atribut typu k označení, že lze serializovat instance tohoto typu. A <xref:System.Runtime.Serialization.SerializationException> je vyvolána výjimka, pokud při pokusu o serializaci, ale typ nemá <xref:System.SerializableAttribute> atribut.  
  
 Pokud nechcete, aby pole v rámci vaší třídě může být serializovatelný, použije <xref:System.NonSerializedAttribute> atribut. Obsahuje-li pole serializovatelného typu ukazatel, popisovač nebo některé datová struktura, která je specifická pro konkrétní prostředí a pole nemůže být rekonstituován smysluplně v jiném prostředí, můžete chtít provést neserializovatelné.  
  
 Pokud serializovaná třídy obsahuje odkazy na objekty jiné třídy, které jsou označeny <xref:System.SerializableAttribute>, tyto objekty se také serializovat.  
  
## <a name="binary-and-xml-serialization"></a>Binární serializace a serializace XML  
 Binární soubor nebo serializace XML lze použít. V binární serializace všechny členy, včetně těch, které jsou jen pro čtení, serializují a výkon je zvýšen. Serializace XML obsahuje kód lépe čitelný, jakož i větší flexibilitu využití pro zajištění spolupráce a sdílení objektu.  
  
### <a name="binary-serialization"></a>Binární serializace  
 Binární serializace používá k vytvoření compact serializace pro použití jako úložiště nebo síťové sokety datové proudy binární kódování.  
  
### <a name="xml-serialization"></a>Serializace XML  
 Serializace XML serializuje veřejné polí a vlastností objektu, nebo parametry a návratovými hodnotami metod do datový proud XML, který odpovídá určitého dokumentu schématu XML definice jazyk (XSD). Výsledky serializace XML v silného typu třídy s veřejné vlastnosti a pole, které jsou převedeny na XML. <xref:System.Xml.Serialization> obsahuje třídy, které jsou potřebné pro serializaci a deserializaci XML.  
  
 Pokud chcete řídit způsob, jakým můžete použít atributy do třídy a členové <xref:System.Xml.Serialization.XmlSerializer> serializuje a deserializuje instance třídy.  
  
## <a name="basic-and-custom-serialization"></a>Základní a vlastní serializace  
 Serializace lze provést dvěma způsoby, základní a vlastní. Základní serializace rozhraní .NET Framework používá k serializaci objektu automaticky.  
  
### <a name="basic-serialization"></a>Základní serializace  
 Jediným požadavkem v základní serializace je, že objekt má <xref:System.SerializableAttribute> atribut. <xref:System.NonSerializedAttribute> Je možné zabránit serializována konkrétních polí.  
  
 Pokud používáte základní serializace, Správa verzí objektů může způsobovat problémy, v takovém případě může být vhodnější než vlastní serializace. Základní serializace je nejjednodušší způsob, jak provést serializace, ale neposkytuje velkou kontrolu nad tímto procesem.  
  
### <a name="custom-serialization"></a>Vlastní serializace  
 Ve vlastní serializace je zadat přesně objektů, které bude serializována a jak provést. Musí být třída označena <xref:System.SerializableAttribute> a implementovat <xref:System.Runtime.Serialization.ISerializable> rozhraní.  
  
 Pokud chcete, aby váš objekt mohl deserializovat vlastní způsobem, je nutné použít vlastního konstruktoru.  
  
## <a name="designer-serialization"></a>Serializace s použitím návrháře  
 Serializace návrháře je zvláštní forma serializace, která zahrnuje druh objektu trvalost obvykle spojené s vývojovými nástroji. Návrháře serializace je proces převodu grafu objektu do zdrojového souboru, který lze později obnovit grafu objektů. Zdrojový soubor může obsahovat kód, značek nebo dokonce i informace o tabulce SQL.  
  
## <a name="BKMK_RelatedTopics"></a> Související témata a příklady  
 [Návod: Uchování objektu v sadě Visual Studio (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/walkthrough-persisting-an-object-in-visual-studio.md)  
 Ukazuje, jak serializace může být použita k uchování dat objektu mezi instancemi, umožňuje uložení hodnot a načíst je dalším je vytvořena instance objektu.  
  
 [Postupy: Čtení dat objektů ze souboru XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)  
 Znázorňuje způsob čtení dat objektů, které se předtím zapsala do souboru XML pomocí <xref:System.Xml.Serialization.XmlSerializer> třídy.  
  
 [Postupy: Zápis dat objektů do souboru XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)  
 Ukazuje, jak zapsat objekt ze třídy do souboru XML pomocí <xref:System.Xml.Serialization.XmlSerializer> třídy.
