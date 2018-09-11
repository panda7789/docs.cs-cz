---
title: Řízení serializace XML pomocí atributů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- classes, serializing
- XML serialization, examples
- derived classes, serializing
- arrays, serializing
- XML serialization, attributes
- preventing serialization
- attributes [.NET Framework], XML serialization
- serialization, examples
- serialization, attributes
ms.assetid: 47d4c39d-30e1-4c7b-8a2e-301325390647
ms.openlocfilehash: 28c7ebe1de3adb92e531597027e4b8bb7a63294c
ms.sourcegitcommit: 67de6cb5dd66a19f2180ba7e4d7aecc697f8a963
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44342469"
---
# <a name="controlling-xml-serialization-using-attributes"></a>Řízení serializace XML pomocí atributů

Atributy lze použít k řízení XML serializace objektu nebo k vytvoření alternativní datový proud XML ze stejné sady tříd. Další informace o vytváření alternativní datový proud XML, naleznete v tématu [postupy: určení alternativního názvu elementu pro XML Stream](how-to-specify-an-alternate-element-name-for-an-xml-stream.md).

> [!NOTE]
> Pokud XML generované musí odpovídat část 5 World Wide Web Consortium (W3C) dokumentu s názvem [jednoduchý objekt přístup protokolu (SOAP) 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/), použijte atributy uvedené v [atributy, že ovládací prvek kódovaný SOAP Serializace](attributes-that-control-encoded-soap-serialization.md).

Ve výchozím nastavení je název elementu XML určen název třída nebo člen. Jednoduchá třída s názvem `Book`, pole s názvem `ISBN` způsobí značku element XML \<ISBN >, jak je znázorněno v následujícím příkladu.

```vb
Public Class Book
    Public ISBN As String
End Class
' When an instance of the Book class is serialized, it might
' produce this XML:
' <ISBN>1234567890</ISBN>.
```

```csharp
public class Book
{
    public string ISBN;
}
// When an instance of the Book class is serialized, it might
// produce this XML:
// <ISBN>1234567890</ISBN>.
```

Toto výchozí chování lze změnit, pokud chcete zadat nový název elementu. Následující kód ukazuje, jak atribut umožňuje to nastavením <xref:System.Xml.Serialization.XmlElementAttribute.ElementName%2A> vlastnost <xref:System.Xml.Serialization.XmlElementAttribute>.

```vb
Public Class TaxRates
   < XmlElement(ElementName = "TaxRate")> _
    Public ReturnTaxRate As Decimal
End Class
```

```csharp
public class TaxRates {
    [XmlElement(ElementName = "TaxRate")]
    public decimal ReturnTaxRate;
}
```

Další informace o atributech najdete v tématu [atributy](../../../docs/standard/attributes/index.md). Seznam atributů řídících serializaci XML, naleznete v tématu [atributy, které ovládací prvek XML serializace](attributes-that-control-xml-serialization.md).

## <a name="controlling-array-serialization"></a>Řízení serializace pole

<xref:System.Xml.Serialization.XmlArrayAttribute> a <xref:System.Xml.Serialization.XmlArrayItemAttribute> atributy jsou určeny k řízení serializace pole. Pomocí těchto atributů, můžete upravit název elementu, obor názvů a datový typ schématu XML (XSD) (jak jsou definovány v dokumentu W3c [www.w3.org] s názvem "XML schématu část 2: datové typy"). Můžete také určit typy, které mohou být zahrnuty do pole.

<xref:System.Xml.Serialization.XmlArrayAttribute> Určí vlastnosti nadřazeného elementu XML, když je serializována pole. Například ve výchozím nastavení, serializací pole níže bude mít za následek element XML s názvem `Employees`. `Employees` Element bude obsahovat několik elementů s názvem po typ pole `Employee`.

```vb
Public Class Group
    Public Employees() As Employee
End Class
Public Class Employee
    Public Name As String
End Class
```

```csharp
public class Group {
    public Employee[] Employees;
}
public class Employee {
    public string Name;
}
```

Serializovanou instanci může vypadat takto.

```xml
<Group>
<Employees>
    <Employee>
        <Name>Haley</Name>
    </Employee>
</Employees>
</Group>
```

Použitím <xref:System.Xml.Serialization.XmlArrayAttribute>, můžete změnit název elementu XML následujícím způsobem.

```vb
Public Class Group
    <XmlArray("TeamMembers")> _
    Public Employees() As Employee
End Class
```

```csharp
public class Group {
    [XmlArray("TeamMembers")]
    public Employee[] Employees;
}
```

Výsledný XML může vypadat takto.

```xml
<Group>
<TeamMembers>
    <Employee>
        <Name>Haley</Name>
    </Employee>
</TeamMembers>
</Group>
```

<xref:System.Xml.Serialization.XmlArrayItemAttribute>, Na druhé straně řídí, jak lze serializovat položky obsažené v poli. Všimněte si, že je atribut použit na pole, který vrací pole.

```vb
Public Class Group
    <XmlArrayItem("MemberName")> _
    Public Employee() As Employees
End Class
```

```csharp
public class Group {
    [XmlArrayItem("MemberName")]
    public Employee[] Employees;
}
```

Výsledný XML může vypadat takto.

```xml
<Group>
<Employees>
    <MemberName>Haley</MemberName>
</Employees>
</Group>
```

## <a name="serializing-derived-classes"></a>Serializace odvozené třídy

Další používání <xref:System.Xml.Serialization.XmlArrayItemAttribute> je umožnit serializace odvozené třídy. Můžete například další třídu s názvem `Manager` která je odvozena od `Employee` mohou být přidány do předchozího příkladu. Pokud se nevztahují <xref:System.Xml.Serialization.XmlArrayItemAttribute>, kód se nezdaří za běhu, protože typ odvozené třídy nebude rozpoznán. Chcete-li to napravit, použijte atribut dvakrát, každé nastavení času <xref:System.Xml.Serialization.XmlArrayItemAttribute.Type%2A> vlastnost pro každý přijatelné typ (základní a odvozené).

```vb
Public Class Group
    <XmlArrayItem(Type:=GetType(Employee)), _
    XmlArrayItem(Type:=GetType(Manager))> _
    Public Employees() As Employee
End Class
Public Class Employee
    Public Name As String
End Class
Public Class Manager
Inherits Employee
    Public Level As Integer
End Class
```

```csharp
public class Group {
    [XmlArrayItem(Type = typeof(Employee)),
    XmlArrayItem(Type = typeof(Manager))]
    public Employee[] Employees;
}
public class Employee {
    public string Name;
}
public class Manager:Employee {
    public int Level;
}
```

Serializovanou instanci může vypadat takto.

```xml
<Group>
<Employees>
    <Employee>
        <Name>Haley</Name>
    </Employee>
    <Employee xsi:type = "Manager">
        <Name>Ann</Name>
        <Level>3</Level>
    <Employee>
</Employees>
</Group>
```

## <a name="serializing-an-array-as-a-sequence-of-elements"></a>Serializace pole jako posloupnost elementy

Můžete také serializovat pole jako plochý sekvence elementů XML použitím <xref:System.Xml.Serialization.XmlElementAttribute> na pole vrací pole následujícím způsobem.

```vb
Public Class Group
    <XmlElement> _
    Public Employees() As Employee
End Class
```

```csharp
public class Group {
    [XmlElement]
    public Employee[] Employees;
}
```

Serializovanou instanci může vypadat takto.

```xml
<Group>
<Employees>
    <Name>Haley</Name>
</Employees>
<Employees>
    <Name>Noriko</Name>
</Employees>
<Employees>
    <Name>Marco</Name>
</Employees>
</Group>
```

Jiný způsob k rozlišení dvou datové proudy XML je použít nástroj definici schématu XML ke generování soubory dokumentů schématu XML (XSD) z zkompilovaný kód. (Další podrobnosti o používání nástroje najdete v tématu [nástroj pro definici schématu XML a serializace XML](the-xml-schema-definition-tool-and-xml-serialization.md).) Při použití žádný atribut na pole, schéma popisuje element následujícím způsobem.

```xml
<xs:element minOccurs="0" maxOccurs ="1" name="Employees" type="ArrayOfEmployee" />
```

Pokud <xref:System.Xml.Serialization.XmlElementAttribute> se použije k poli, výsledný schéma popisuje element takto.

```xml
<xs:element minOccurs="0" maxOccurs="unbounded" name="Employees" type="Employee" /> 
```

## <a name="serializing-an-arraylist"></a>Serializace ArrayList

<xref:System.Collections.ArrayList> Třídy mohou obsahovat kolekce rozmanitý objektů. Proto můžete použít <xref:System.Collections.ArrayList> podobně jako pomocí pole. Místo vytváření pole, které vrátí pole objektů typem, však můžete vytvořit pole, které vrátí jednu <xref:System.Collections.ArrayList>. Však stejně jako u pole, musí informovat <xref:System.Xml.Serialization.XmlSerializer> typů objektů <xref:System.Collections.ArrayList> obsahuje. K provedení této operace, přiřazení více instancí <xref:System.Xml.Serialization.XmlElementAttribute> na pole, jak je znázorněno v následujícím příkladu.

```vb
Public Class Group
    <XmlElement(Type:=GetType(Employee)), _
    XmlElement(Type:=GetType(Manager))> _
    Public Info As ArrayList
End Class
```

```csharp
public class Group {
    [XmlElement(Type = typeof(Employee)), 
    XmlElement(Type = typeof(Manager))]
    public ArrayList Info;
}
```

## <a name="controlling-serialization-of-classes-using-xmlrootattribute-and-xmltypeattribute"></a>Řízení serializace tříd pomocí XmlRootAttribute a XmlTypeAttribute

Dva atributy, které mohou být použity na třídu (a pouze třídu): <xref:System.Xml.Serialization.XmlRootAttribute> a <xref:System.Xml.Serialization.XmlTypeAttribute>. Tyto atributy jsou velmi podobné. <xref:System.Xml.Serialization.XmlRootAttribute> Lze použít pouze jednu třídu: třída, že při serializován, představuje dokumentu XML je otevření a zavření element – jinými slovy, kořenový element. <xref:System.Xml.Serialization.XmlTypeAttribute>, Na druhé straně, lze použít na všechny třídy, včetně kořenová třída.

Například ve výše uvedených příkladech `Group` třída je kořenová třída a všechny veřejné polí a vlastností stát elementů XML nalezen v dokumentu XML. Proto může být pouze jeden kořenový třídy. Použitím <xref:System.Xml.Serialization.XmlRootAttribute>, můžete řídit datový proud XML generovaných <xref:System.Xml.Serialization.XmlSerializer>. Můžete například změnit název elementu a obor názvů.

<xref:System.Xml.Serialization.XmlTypeAttribute> Umožňuje řídit schéma vygenerovaný kód XML. Tato možnost je užitečná, pokud je třeba publikovat schématu pomocí webové služby XML. Následující příklad se vztahuje i <xref:System.Xml.Serialization.XmlTypeAttribute> a <xref:System.Xml.Serialization.XmlRootAttribute> do stejné třídy.

```vb
<XmlRoot("NewGroupName"), _
XmlType("NewTypeName")> _
Public Class Group
    Public Employees() As Employee
End Class
```

```csharp
[XmlRoot("NewGroupName")]
[XmlType("NewTypeName")]
public class Group {
    public Employee[] Employees;
}
```

Pokud tato třída je kompilována a nástroj pro definici schématu XML se používá ke generování jeho schématu, by najít následující XML popisující `Group`.

```xml
<xs:element name="NewGroupName" type="NewTypeName">
```

Naopak, pokud byly k serializaci instancí třídy pouze `NewGroupName` bude nalezen v dokumentu XML.

```xml
<NewGroupName>
    . . .
</NewGroupName>
```

## <a name="preventing-serialization-with-the-xmlignoreattribute"></a>Prevence serializace s XmlIgnoreAttribute

Mohou nastat situace, když veřejné vlastnosti nebo pole nemusí být serializován. Můžete například pole nebo vlastnost může obsahovat metadat. V takových případech, použije <xref:System.Xml.Serialization.XmlIgnoreAttribute> na pole nebo vlastnost a <xref:System.Xml.Serialization.XmlSerializer> vynechá nad ním.

## <a name="see-also"></a>Viz také:

- [Seznam atributů řídících serializaci XML](attributes-that-control-xml-serialization.md)  
- [Seznam atributů řídících serializaci zakódovanou v protokolu SOAP](attributes-that-control-encoded-soap-serialization.md)  
- [Představení serializace XML](introducing-xml-serialization.md)  
- [Příklady serializace XML](examples-of-xml-serialization.md)  
- [Postupy: Zadání alternativního názvu elementu pro XML stream](how-to-specify-an-alternate-element-name-for-an-xml-stream.md)  
- [Postupy: Serializace objektu](how-to-serialize-an-object.md)  
- [Postupy: Deserializace objektu](how-to-deserialize-an-object.md)  
