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
ms.openlocfilehash: e11152dc626b1e3619b9ecbc04d8a237ca9f13d3
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80248040"
---
# <a name="controlling-xml-serialization-using-attributes"></a><span data-ttu-id="e5e0f-102">Řízení serializace XML pomocí atributů</span><span class="sxs-lookup"><span data-stu-id="e5e0f-102">Controlling XML Serialization Using Attributes</span></span>

<span data-ttu-id="e5e0f-103">Atributy lze použít k řízení XML serializace objektu nebo k vytvoření alternativní datový proud XML ze stejné sady tříd.</span><span class="sxs-lookup"><span data-stu-id="e5e0f-103">Attributes can be used to control the XML serialization of an object or to create an alternate XML stream from the same set of classes.</span></span> <span data-ttu-id="e5e0f-104">Další podrobnosti o vytvoření alternativního datového proudu XML najdete v [tématu Postup: Zadání názvu alternativního prvku datového proudu XML](how-to-specify-an-alternate-element-name-for-an-xml-stream.md).</span><span class="sxs-lookup"><span data-stu-id="e5e0f-104">For more details about creating an alternate XML stream, see [How to: Specify an Alternate Element Name for an XML Stream](how-to-specify-an-alternate-element-name-for-an-xml-stream.md).</span></span>

> [!NOTE]
> <span data-ttu-id="e5e0f-105">Pokud musí generovaný kód XML odpovídat části 5 dokumentu W3C (World Wide Web Consortium) s názvem [Simple Object Access Protocol (SOAP) 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/), použijte atributy uvedené v části [Atributy, které řídí kódovanou serializaci SOAP](attributes-that-control-encoded-soap-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="e5e0f-105">If the XML generated must conform to section 5 of the World Wide Web Consortium (W3C) document titled [Simple Object Access Protocol (SOAP) 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/), use the attributes listed in [Attributes That Control Encoded SOAP Serialization](attributes-that-control-encoded-soap-serialization.md).</span></span>

<span data-ttu-id="e5e0f-106">Ve výchozím nastavení je název elementu XML určen název třída nebo člen.</span><span class="sxs-lookup"><span data-stu-id="e5e0f-106">By default, an XML element name is determined by the class or member name.</span></span> <span data-ttu-id="e5e0f-107">V jednoduché třídě `Book`s názvem `ISBN` pole s názvem \<vytvoří značku elementu XML ISBN>, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="e5e0f-107">In a simple class named `Book`, a field named `ISBN` will produce an XML element tag \<ISBN>, as shown in the following example.</span></span>

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

<span data-ttu-id="e5e0f-108">Toto výchozí chování lze změnit, pokud chcete zadat nový název elementu.</span><span class="sxs-lookup"><span data-stu-id="e5e0f-108">This default behavior can be changed if you want to give the element a new name.</span></span> <span data-ttu-id="e5e0f-109">Následující kód ukazuje, jak atribut umožňuje to nastavením <xref:System.Xml.Serialization.XmlElementAttribute.ElementName%2A> vlastnost <xref:System.Xml.Serialization.XmlElementAttribute>.</span><span class="sxs-lookup"><span data-stu-id="e5e0f-109">The following code shows how an attribute enables this by setting the <xref:System.Xml.Serialization.XmlElementAttribute.ElementName%2A> property of a <xref:System.Xml.Serialization.XmlElementAttribute>.</span></span>

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

<span data-ttu-id="e5e0f-110">Další informace o atributech naleznete v [tématu Atributy](../../../docs/standard/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="e5e0f-110">For more information about attributes, see [Attributes](../../../docs/standard/attributes/index.md).</span></span> <span data-ttu-id="e5e0f-111">Seznam atributů, které řídí serializaci XML, naleznete v [tématu Atributy, které řídí serializaci XML](attributes-that-control-xml-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="e5e0f-111">For a list of attributes that control XML serialization, see [Attributes That Control XML Serialization](attributes-that-control-xml-serialization.md).</span></span>

## <a name="controlling-array-serialization"></a><span data-ttu-id="e5e0f-112">Řízení serializace pole</span><span class="sxs-lookup"><span data-stu-id="e5e0f-112">Controlling Array Serialization</span></span>

<span data-ttu-id="e5e0f-113"><xref:System.Xml.Serialization.XmlArrayAttribute> a <xref:System.Xml.Serialization.XmlArrayItemAttribute> atributy jsou určeny k řízení serializace pole.</span><span class="sxs-lookup"><span data-stu-id="e5e0f-113">The <xref:System.Xml.Serialization.XmlArrayAttribute> and the <xref:System.Xml.Serialization.XmlArrayItemAttribute> attributes are designed to control the serialization of arrays.</span></span> <span data-ttu-id="e5e0f-114">Pomocí těchto atributů, můžete upravit název elementu, obor názvů a datový typ schématu XML (XSD) (jak jsou definovány v dokumentu W3c [www.w3.org] s názvem "XML schématu část 2: datové typy").</span><span class="sxs-lookup"><span data-stu-id="e5e0f-114">Using these attributes, you can control the element name, namespace, and XML Schema (XSD) data type (as defined in the World Wide Web Consortium [www.w3.org] document titled "XML Schema Part 2: Datatypes").</span></span> <span data-ttu-id="e5e0f-115">Můžete také určit typy, které mohou být zahrnuty do pole.</span><span class="sxs-lookup"><span data-stu-id="e5e0f-115">You can also specify the types that can be included in an array.</span></span>

<span data-ttu-id="e5e0f-116"><xref:System.Xml.Serialization.XmlArrayAttribute> Určí vlastnosti nadřazeného elementu XML, když je serializována pole.</span><span class="sxs-lookup"><span data-stu-id="e5e0f-116">The <xref:System.Xml.Serialization.XmlArrayAttribute> will determine the properties of the enclosing XML element that results when an array is serialized.</span></span> <span data-ttu-id="e5e0f-117">Například ve výchozím nastavení, serializací pole níže bude mít za následek element XML s názvem `Employees`.</span><span class="sxs-lookup"><span data-stu-id="e5e0f-117">For example, by default, serializing the array below will result in an XML element named `Employees`.</span></span> <span data-ttu-id="e5e0f-118">`Employees` Element bude obsahovat několik elementů s názvem po typ pole `Employee`.</span><span class="sxs-lookup"><span data-stu-id="e5e0f-118">The `Employees` element will contain a series of elements named after the array type `Employee`.</span></span>

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

<span data-ttu-id="e5e0f-119">Serializovanou instanci může vypadat takto.</span><span class="sxs-lookup"><span data-stu-id="e5e0f-119">A serialized instance might resemble the following.</span></span>

```xml
<Group>
<Employees>
    <Employee>
        <Name>Haley</Name>
    </Employee>
</Employees>
</Group>
```

<span data-ttu-id="e5e0f-120">Použitím <xref:System.Xml.Serialization.XmlArrayAttribute>, můžete změnit název elementu XML následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="e5e0f-120">By applying a <xref:System.Xml.Serialization.XmlArrayAttribute>, you can change the name of the XML element, as follows.</span></span>

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

<span data-ttu-id="e5e0f-121">Výsledný XML může vypadat takto.</span><span class="sxs-lookup"><span data-stu-id="e5e0f-121">The resulting XML might resemble the following.</span></span>

```xml
<Group>
<TeamMembers>
    <Employee>
        <Name>Haley</Name>
    </Employee>
</TeamMembers>
</Group>
```

<span data-ttu-id="e5e0f-122"><xref:System.Xml.Serialization.XmlArrayItemAttribute>, Na druhé straně řídí, jak lze serializovat položky obsažené v poli.</span><span class="sxs-lookup"><span data-stu-id="e5e0f-122">The <xref:System.Xml.Serialization.XmlArrayItemAttribute>, on the other hand, controls how the items contained in the array are serialized.</span></span> <span data-ttu-id="e5e0f-123">Všimněte si, že je atribut použit na pole, který vrací pole.</span><span class="sxs-lookup"><span data-stu-id="e5e0f-123">Note that the attribute is applied to the field returning the array.</span></span>

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

<span data-ttu-id="e5e0f-124">Výsledný XML může vypadat takto.</span><span class="sxs-lookup"><span data-stu-id="e5e0f-124">The resulting XML might resemble the following.</span></span>

```xml
<Group>
<Employees>
    <MemberName>Haley</MemberName>
</Employees>
</Group>
```

## <a name="serializing-derived-classes"></a><span data-ttu-id="e5e0f-125">Serializace odvozené třídy</span><span class="sxs-lookup"><span data-stu-id="e5e0f-125">Serializing Derived Classes</span></span>

<span data-ttu-id="e5e0f-126">Další používání <xref:System.Xml.Serialization.XmlArrayItemAttribute> je umožnit serializace odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="e5e0f-126">Another use of the <xref:System.Xml.Serialization.XmlArrayItemAttribute> is to allow the serialization of derived classes.</span></span> <span data-ttu-id="e5e0f-127">Můžete například další třídu s názvem `Manager` která je odvozena od `Employee` mohou být přidány do předchozího příkladu.</span><span class="sxs-lookup"><span data-stu-id="e5e0f-127">For example, another class named `Manager` that derives from `Employee` can be added to the previous example.</span></span> <span data-ttu-id="e5e0f-128">Pokud se nevztahují <xref:System.Xml.Serialization.XmlArrayItemAttribute>, kód se nezdaří za běhu, protože typ odvozené třídy nebude rozpoznán.</span><span class="sxs-lookup"><span data-stu-id="e5e0f-128">If you do not apply the <xref:System.Xml.Serialization.XmlArrayItemAttribute>, the code will fail at run time because the derived class type will not be recognized.</span></span> <span data-ttu-id="e5e0f-129">Chcete-li to napravit, použijte atribut dvakrát, každé nastavení času <xref:System.Xml.Serialization.XmlArrayItemAttribute.Type%2A> vlastnost pro každý přijatelné typ (základní a odvozené).</span><span class="sxs-lookup"><span data-stu-id="e5e0f-129">To remedy this, apply the attribute twice, each time setting the <xref:System.Xml.Serialization.XmlArrayItemAttribute.Type%2A> property for each acceptable type (base and derived).</span></span>

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

<span data-ttu-id="e5e0f-130">Serializovanou instanci může vypadat takto.</span><span class="sxs-lookup"><span data-stu-id="e5e0f-130">A serialized instance might resemble the following.</span></span>

```xml
<Group>
<Employees>
    <Employee>
        <Name>Haley</Name>
    </Employee>
    <Employee xsi:type = "Manager">
        <Name>Ann</Name>
        <Level>3</Level>
    </Employee>
</Employees>
</Group>
```

## <a name="serializing-an-array-as-a-sequence-of-elements"></a><span data-ttu-id="e5e0f-131">Serializace pole jako posloupnost elementy</span><span class="sxs-lookup"><span data-stu-id="e5e0f-131">Serializing an Array as a Sequence of Elements</span></span>

<span data-ttu-id="e5e0f-132">Můžete také serializovat pole jako plochý sekvence elementů XML použitím <xref:System.Xml.Serialization.XmlElementAttribute> na pole vrací pole následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="e5e0f-132">You can also serialize an array as a flat sequence of XML elements by applying a <xref:System.Xml.Serialization.XmlElementAttribute> to the field returning the array as follows.</span></span>

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

<span data-ttu-id="e5e0f-133">Serializovanou instanci může vypadat takto.</span><span class="sxs-lookup"><span data-stu-id="e5e0f-133">A serialized instance might resemble the following.</span></span>

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

<span data-ttu-id="e5e0f-134">Jiný způsob k rozlišení dvou datové proudy XML je použít nástroj definici schématu XML ke generování soubory dokumentů schématu XML (XSD) z zkompilovaný kód.</span><span class="sxs-lookup"><span data-stu-id="e5e0f-134">Another way to differentiate the two XML streams is to use the XML Schema Definition tool to generate the XML Schema (XSD) document files from the compiled code.</span></span> <span data-ttu-id="e5e0f-135">(Další podrobnosti o použití nástroje naleznete v [tématu Nástroj pro definici schématu XML a Serializace XML](the-xml-schema-definition-tool-and-xml-serialization.md).) Pokud není pro pole použit žádný atribut, schéma popisuje prvek následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="e5e0f-135">(For more details on using the tool, see [The XML Schema Definition Tool and XML Serialization](the-xml-schema-definition-tool-and-xml-serialization.md).) When no attribute is applied to the field, the schema describes the element in the following manner.</span></span>

```xml
<xs:element minOccurs="0" maxOccurs ="1" name="Employees" type="ArrayOfEmployee" />
```

<span data-ttu-id="e5e0f-136">Pokud <xref:System.Xml.Serialization.XmlElementAttribute> se použije k poli, výsledný schéma popisuje element takto.</span><span class="sxs-lookup"><span data-stu-id="e5e0f-136">When the <xref:System.Xml.Serialization.XmlElementAttribute> is applied to the field, the resulting schema describes the element as follows.</span></span>

```xml
<xs:element minOccurs="0" maxOccurs="unbounded" name="Employees" type="Employee" />
```

## <a name="serializing-an-arraylist"></a><span data-ttu-id="e5e0f-137">Serializace ArrayList</span><span class="sxs-lookup"><span data-stu-id="e5e0f-137">Serializing an ArrayList</span></span>

<span data-ttu-id="e5e0f-138"><xref:System.Collections.ArrayList> Třídy mohou obsahovat kolekce rozmanitý objektů.</span><span class="sxs-lookup"><span data-stu-id="e5e0f-138">The <xref:System.Collections.ArrayList> class can contain a collection of diverse objects.</span></span> <span data-ttu-id="e5e0f-139">Proto můžete použít <xref:System.Collections.ArrayList> podobně jako pomocí pole.</span><span class="sxs-lookup"><span data-stu-id="e5e0f-139">You can therefore use a <xref:System.Collections.ArrayList> much as you use an array.</span></span> <span data-ttu-id="e5e0f-140">Místo vytváření pole, které vrátí pole objektů typem, však můžete vytvořit pole, které vrátí jednu <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="e5e0f-140">Instead of creating a field that returns an array of typed objects, however, you can create a field that returns a single <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="e5e0f-141">Však stejně jako u pole, musí informovat <xref:System.Xml.Serialization.XmlSerializer> typů objektů <xref:System.Collections.ArrayList> obsahuje.</span><span class="sxs-lookup"><span data-stu-id="e5e0f-141">However, as with arrays, you must inform the <xref:System.Xml.Serialization.XmlSerializer> of the types of objects the <xref:System.Collections.ArrayList> contains.</span></span> <span data-ttu-id="e5e0f-142">K provedení této operace, přiřazení více instancí <xref:System.Xml.Serialization.XmlElementAttribute> na pole, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="e5e0f-142">To accomplish this, assign multiple instances of the <xref:System.Xml.Serialization.XmlElementAttribute> to the field, as shown in the following example.</span></span>

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

## <a name="controlling-serialization-of-classes-using-xmlrootattribute-and-xmltypeattribute"></a><span data-ttu-id="e5e0f-143">Řízení serializace tříd pomocí XmlRootAttribute a XmlTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="e5e0f-143">Controlling Serialization of Classes Using XmlRootAttribute and XmlTypeAttribute</span></span>

<span data-ttu-id="e5e0f-144">Dva atributy, které mohou být použity na třídu (a pouze třídu): <xref:System.Xml.Serialization.XmlRootAttribute> a <xref:System.Xml.Serialization.XmlTypeAttribute>.</span><span class="sxs-lookup"><span data-stu-id="e5e0f-144">There are two attributes that can be applied to a class (and only a class): <xref:System.Xml.Serialization.XmlRootAttribute> and <xref:System.Xml.Serialization.XmlTypeAttribute>.</span></span> <span data-ttu-id="e5e0f-145">Tyto atributy jsou velmi podobné.</span><span class="sxs-lookup"><span data-stu-id="e5e0f-145">These attributes are very similar.</span></span> <span data-ttu-id="e5e0f-146"><xref:System.Xml.Serialization.XmlRootAttribute> Lze použít pouze jednu třídu: třída, že při serializován, představuje dokumentu XML je otevření a zavření element – jinými slovy, kořenový element.</span><span class="sxs-lookup"><span data-stu-id="e5e0f-146">The <xref:System.Xml.Serialization.XmlRootAttribute> can be applied to only one class: the class that, when serialized, represents the XML document's opening and closing element—in other words, the root element.</span></span> <span data-ttu-id="e5e0f-147"><xref:System.Xml.Serialization.XmlTypeAttribute>, Na druhé straně, lze použít na všechny třídy, včetně kořenová třída.</span><span class="sxs-lookup"><span data-stu-id="e5e0f-147">The <xref:System.Xml.Serialization.XmlTypeAttribute>, on the other hand, can be applied to any class, including the root class.</span></span>

<span data-ttu-id="e5e0f-148">Například ve výše uvedených příkladech `Group` třída je kořenová třída a všechny veřejné polí a vlastností stát elementů XML nalezen v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="e5e0f-148">For example, in the previous examples, the `Group` class is the root class, and all its public fields and properties become the XML elements found in the XML document.</span></span> <span data-ttu-id="e5e0f-149">Proto může být pouze jeden kořenový třídy.</span><span class="sxs-lookup"><span data-stu-id="e5e0f-149">Therefore, there can be only one root class.</span></span> <span data-ttu-id="e5e0f-150">Použitím <xref:System.Xml.Serialization.XmlRootAttribute>, můžete řídit datový proud XML generovaných <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="e5e0f-150">By applying the <xref:System.Xml.Serialization.XmlRootAttribute>, you can control the XML stream generated by the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="e5e0f-151">Můžete například změnit název elementu a obor názvů.</span><span class="sxs-lookup"><span data-stu-id="e5e0f-151">For example, you can change the element name and namespace.</span></span>

<span data-ttu-id="e5e0f-152"><xref:System.Xml.Serialization.XmlTypeAttribute> Umožňuje řídit schéma vygenerovaný kód XML.</span><span class="sxs-lookup"><span data-stu-id="e5e0f-152">The <xref:System.Xml.Serialization.XmlTypeAttribute> allows you to control the schema of the generated XML.</span></span> <span data-ttu-id="e5e0f-153">Tato možnost je užitečná, pokud je třeba publikovat schématu pomocí webové služby XML.</span><span class="sxs-lookup"><span data-stu-id="e5e0f-153">This capability is useful when you need to publish the schema through an XML Web service.</span></span> <span data-ttu-id="e5e0f-154">Následující příklad se vztahuje i <xref:System.Xml.Serialization.XmlTypeAttribute> a <xref:System.Xml.Serialization.XmlRootAttribute> do stejné třídy.</span><span class="sxs-lookup"><span data-stu-id="e5e0f-154">The following example applies both the <xref:System.Xml.Serialization.XmlTypeAttribute> and the <xref:System.Xml.Serialization.XmlRootAttribute> to the same class.</span></span>

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

<span data-ttu-id="e5e0f-155">Pokud tato třída je kompilována a nástroj pro definici schématu XML se používá ke generování jeho schématu, by najít následující XML popisující `Group`.</span><span class="sxs-lookup"><span data-stu-id="e5e0f-155">If this class is compiled, and the XML Schema Definition tool is used to generate its schema, you would find the following XML describing `Group`.</span></span>

```xml
<xs:element name="NewGroupName" type="NewTypeName" />
```

<span data-ttu-id="e5e0f-156">Naopak, pokud byly k serializaci instancí třídy pouze `NewGroupName` bude nalezen v dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="e5e0f-156">In contrast, if you were to serialize an instance of the class, only `NewGroupName` would be found in the XML document.</span></span>

```xml
<NewGroupName>
    . . .
</NewGroupName>
```

## <a name="preventing-serialization-with-the-xmlignoreattribute"></a><span data-ttu-id="e5e0f-157">Prevence serializace s XmlIgnoreAttribute</span><span class="sxs-lookup"><span data-stu-id="e5e0f-157">Preventing Serialization with the XmlIgnoreAttribute</span></span>

<span data-ttu-id="e5e0f-158">Mohou nastat situace, když veřejné vlastnosti nebo pole nemusí být serializován.</span><span class="sxs-lookup"><span data-stu-id="e5e0f-158">There might be situations when a public property or field does not need to be serialized.</span></span> <span data-ttu-id="e5e0f-159">Můžete například pole nebo vlastnost může obsahovat metadat.</span><span class="sxs-lookup"><span data-stu-id="e5e0f-159">For example, a field or property could be used to contain metadata.</span></span> <span data-ttu-id="e5e0f-160">V takových případech, použije <xref:System.Xml.Serialization.XmlIgnoreAttribute> na pole nebo vlastnost a <xref:System.Xml.Serialization.XmlSerializer> vynechá nad ním.</span><span class="sxs-lookup"><span data-stu-id="e5e0f-160">In such cases, apply the <xref:System.Xml.Serialization.XmlIgnoreAttribute> to the field or property and the <xref:System.Xml.Serialization.XmlSerializer> will skip over it.</span></span>

## <a name="see-also"></a><span data-ttu-id="e5e0f-161">Viz také</span><span class="sxs-lookup"><span data-stu-id="e5e0f-161">See also</span></span>

- [<span data-ttu-id="e5e0f-162">Atributy, které řídí serializaci XML</span><span class="sxs-lookup"><span data-stu-id="e5e0f-162">Attributes That Control XML Serialization</span></span>](attributes-that-control-xml-serialization.md)
- [<span data-ttu-id="e5e0f-163">Atributy, které řídí serializaci zakódovanou v protokolu SOAP</span><span class="sxs-lookup"><span data-stu-id="e5e0f-163">Attributes That Control Encoded SOAP Serialization</span></span>](attributes-that-control-encoded-soap-serialization.md)
- [<span data-ttu-id="e5e0f-164">Představení serializace XML</span><span class="sxs-lookup"><span data-stu-id="e5e0f-164">Introducing XML Serialization</span></span>](introducing-xml-serialization.md)
- [<span data-ttu-id="e5e0f-165">Příklady serializace XML</span><span class="sxs-lookup"><span data-stu-id="e5e0f-165">Examples of XML Serialization</span></span>](examples-of-xml-serialization.md)
- [<span data-ttu-id="e5e0f-166">Postupy: Zadání alternativního názvu elementu pro XML stream</span><span class="sxs-lookup"><span data-stu-id="e5e0f-166">How to: Specify an Alternate Element Name for an XML Stream</span></span>](how-to-specify-an-alternate-element-name-for-an-xml-stream.md)
- [<span data-ttu-id="e5e0f-167">Postupy: Serializace objektu</span><span class="sxs-lookup"><span data-stu-id="e5e0f-167">How to: Serialize an Object</span></span>](how-to-serialize-an-object.md)
- [<span data-ttu-id="e5e0f-168">Postupy: Deserializace objektu</span><span class="sxs-lookup"><span data-stu-id="e5e0f-168">How to: Deserialize an Object</span></span>](how-to-deserialize-an-object.md)
