---
title: Porovnání webových služeb ASP.NET Web Services s technologií WCF z hlediska vývojových požadavků
ms.date: 03/30/2017
ms.assetid: f362d00e-ce82-484f-9d4f-27e579d5c320
ms.openlocfilehash: e5d249514ecad7507235bb8bd354c80bdc17c5dc
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2019
ms.locfileid: "57679746"
---
# <a name="comparing-aspnet-web-services-to-wcf-based-on-development"></a><span data-ttu-id="e06ef-102">Porovnání webových služeb ASP.NET Web Services s technologií WCF z hlediska vývojových požadavků</span><span class="sxs-lookup"><span data-stu-id="e06ef-102">Comparing ASP.NET Web Services to WCF Based on Development</span></span>

<span data-ttu-id="e06ef-103">Windows Communication Foundation (WCF) je možnost režim kompatibility ASP.NET umožňují aplikacím naprogramovat a nakonfigurované stejně jako webové služby WCF a napodobení jejich chování.</span><span class="sxs-lookup"><span data-stu-id="e06ef-103">Windows Communication Foundation (WCF) has an ASP.NET compatibility mode option to enable WCF applications to be programmed and configured like ASP.NET Web services, and mimic their behavior.</span></span> <span data-ttu-id="e06ef-104">Následující části porovnávají webových služeb ASP.NET a WCF založená na co je potřeba k vývoji aplikací pomocí obou technologií.</span><span class="sxs-lookup"><span data-stu-id="e06ef-104">The following sections compare ASP.NET Web services and WCF based on what is required to develop applications using both technologies.</span></span>

## <a name="data-representation"></a><span data-ttu-id="e06ef-105">Reprezentace dat</span><span class="sxs-lookup"><span data-stu-id="e06ef-105">Data Representation</span></span>

<span data-ttu-id="e06ef-106">Vývoj webové služby s využitím technologie ASP.NET se obvykle začíná definování jakékoli komplexních datových typů, které se má používat služba.</span><span class="sxs-lookup"><span data-stu-id="e06ef-106">The development of a Web service with ASP.NET typically begins with defining any complex data types the service is to use.</span></span> <span data-ttu-id="e06ef-107">Technologie ASP.NET se může spolehnout <xref:System.Xml.Serialization.XmlSerializer> převodu dat reprezentovaný typy rozhraní .NET Framework do formátu XML pro přenos do nebo ze služby a pro převod data přijatá ve formátu XML do objektů .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e06ef-107">ASP.NET relies on the <xref:System.Xml.Serialization.XmlSerializer> to translate data represented by .NET Framework types to XML for transmission to or from a service and to translate data received as XML into .NET Framework objects.</span></span> <span data-ttu-id="e06ef-108">Definování komplexních datových typů, které se má používat službu ASP.NET vyžaduje definici rozhraní .NET Framework třída, která je <xref:System.Xml.Serialization.XmlSerializer> může serializovat do a ze souboru XML.</span><span class="sxs-lookup"><span data-stu-id="e06ef-108">Defining the complex data types that an ASP.NET service is to use requires the definition of .NET Framework classes that the <xref:System.Xml.Serialization.XmlSerializer> can serialize to and from XML.</span></span> <span data-ttu-id="e06ef-109">Takové třídy napsané ručně, nebo generovány z definice typů ve schématu XML pomocí příkazového řádku XML schémat/dat typy podpory nástroje, xsd.exe.</span><span class="sxs-lookup"><span data-stu-id="e06ef-109">Such classes can be written manually, or generated from definitions of the types in XML Schema using the command-line XML Schemas/Data Types Support Utility, xsd.exe.</span></span>

<span data-ttu-id="e06ef-110">Tady je seznam důležitých problémů vědět při definování rozhraní .NET Framework třída, která je <xref:System.Xml.Serialization.XmlSerializer> může serializovat do a ze souboru XML:</span><span class="sxs-lookup"><span data-stu-id="e06ef-110">The following is a list of key issues to know when defining .NET Framework classes that the <xref:System.Xml.Serialization.XmlSerializer> can serialize to and from XML:</span></span>

- <span data-ttu-id="e06ef-111">Pouze veřejné polí a vlastností objektů v rozhraní .NET Framework jsou přeloženy do XML.</span><span class="sxs-lookup"><span data-stu-id="e06ef-111">Only the public fields and properties of .NET Framework objects are translated into XML.</span></span>

- <span data-ttu-id="e06ef-112">Instance třídy kolekce lze serializovat do souboru XML, pouze v případě, že třídy implementovat buď <xref:System.Collections.IEnumerable> nebo <xref:System.Collections.ICollection> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e06ef-112">Instances of collection classes can be serialized into XML only if the classes implement either the <xref:System.Collections.IEnumerable> or <xref:System.Collections.ICollection> interface.</span></span>

- <span data-ttu-id="e06ef-113">Třídy, které implementují <xref:System.Collections.IDictionary> rozhraní, jako například <xref:System.Collections.Hashtable>, nejde serializovat do formátu XML.</span><span class="sxs-lookup"><span data-stu-id="e06ef-113">Classes that implement the <xref:System.Collections.IDictionary> interface, such as <xref:System.Collections.Hashtable>, cannot be serialized into XML.</span></span>

- <span data-ttu-id="e06ef-114">Velké typy v mnoha atributů <xref:System.Xml.Serialization> oboru názvů lze přidat do třídy rozhraní .NET Framework a jeho členy lze řídit, jak jsou reprezentovány instancí třídy ve formátu XML.</span><span class="sxs-lookup"><span data-stu-id="e06ef-114">The great many attribute types in the <xref:System.Xml.Serialization> namespace can be added to a .NET Framework class and its members to control how instances of the class are represented in XML.</span></span>

<span data-ttu-id="e06ef-115">Vývoj aplikací WCF obvykle také začíná definice komplexních typů.</span><span class="sxs-lookup"><span data-stu-id="e06ef-115">WCF application development usually also begins with the definition of complex types.</span></span> <span data-ttu-id="e06ef-116">WCF je třeba použít stejné typy rozhraní .NET Framework jako webové služby ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="e06ef-116">WCF can be made to use the same .NET Framework types as ASP.NET Web services.</span></span>

<span data-ttu-id="e06ef-117">WCF<xref:System.Runtime.Serialization.DataContractAttribute> a <xref:System.Runtime.Serialization.DataMemberAttribute> lze přidat na typy rozhraní .NET Framework označuje, že se instance daného typu, je k serializaci do XML a které konkrétních polích nebo vlastnostech typu jsou serializovaná, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="e06ef-117">The WCF<xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> can be added to .NET Framework types to indicate that instances of the type are to be serialized into XML, and which particular fields or properties of the type are to be serialized, as shown in the following sample code.</span></span>

```csharp
//Example One:
[DataContract]
public class LineItem
{
    [DataMember]
    public string ItemNumber;
    [DataMember]
    public decimal Quantity;
    [DataMember]
    public decimal UnitPrice;
}

//Example Two:
public class LineItem
{
    [DataMember]
    private string itemNumber;
    [DataMember]
    private decimal quantity;
    [DataMember]
    private decimal unitPrice;

    public string ItemNumber
    {
      get
      {
          return this.itemNumber;
      }

      set
      {
          this.itemNumber = value;
      }
    }

    public decimal Quantity
    {
        get
        {
            return this.quantity;
        }

        set
        {
            this.quantity = value;
        }
    }

    public decimal UnitPrice
    {
      get
      {
          return this.unitPrice;
      }

      set
      {
          this.unitPrice = value;
      }
    }
}

//Example Three:
public class LineItem
{
     private string itemNumber;
     private decimal quantity;
     private decimal unitPrice;

     [DataMember]
     public string ItemNumber
     {
       get
       {
          return this.itemNumber;
       }

       set
       {
           this.itemNumber = value;
       }
     }

     [DataMember]
     public decimal Quantity
     {
          get
          {
              return this.quantity;
          }

          set
          {
             this.quantity = value;
          }
     }

     [DataMember]
     public decimal UnitPrice
     {
          get
          {
              return this.unitPrice;
          }

          set
          {
              this.unitPrice = value;
          }
     }
}
```

<span data-ttu-id="e06ef-118"><xref:System.Runtime.Serialization.DataContractAttribute> Znamená, že nula nebo více polí a vlastností typu mají být serializován, zatímco <xref:System.Runtime.Serialization.DataMemberAttribute> označuje, že konkrétní pole nebo vlastnost má být serializován.</span><span class="sxs-lookup"><span data-stu-id="e06ef-118">The <xref:System.Runtime.Serialization.DataContractAttribute> signifies that zero or more of a type’s fields or properties are to be serialized, while the <xref:System.Runtime.Serialization.DataMemberAttribute> indicates that a particular field or property is to be serialized.</span></span> <span data-ttu-id="e06ef-119"><xref:System.Runtime.Serialization.DataContractAttribute> Lze použít u třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="e06ef-119">The <xref:System.Runtime.Serialization.DataContractAttribute> can be applied to a class or structure.</span></span> <span data-ttu-id="e06ef-120"><xref:System.Runtime.Serialization.DataMemberAttribute> Lze použít u pole nebo vlastnost a pole a vlastnosti, ke kterým se atribut používá může být veřejné nebo soukromé.</span><span class="sxs-lookup"><span data-stu-id="e06ef-120">The <xref:System.Runtime.Serialization.DataMemberAttribute> can be applied to a field or a property, and the fields and properties to which the attribute is applied can be either public or private.</span></span> <span data-ttu-id="e06ef-121">Instance typů, které mají <xref:System.Runtime.Serialization.DataContractAttribute> u nich, se nazývají data smluv ve službě WCF.</span><span class="sxs-lookup"><span data-stu-id="e06ef-121">Instances of types that have the <xref:System.Runtime.Serialization.DataContractAttribute> applied to them are referred to as data contracts in WCF.</span></span> <span data-ttu-id="e06ef-122">Jsou serializován do souboru XML pomocí <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="e06ef-122">They are serialized into XML using <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>

<span data-ttu-id="e06ef-123">Tady je seznam důležitých rozdílů mezi použitím nástrojů <xref:System.Runtime.Serialization.DataContractSerializer> a použití <xref:System.Xml.Serialization.XmlSerializer> a různé atributy <xref:System.Xml.Serialization> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e06ef-123">The following is a list of the important differences between using the <xref:System.Runtime.Serialization.DataContractSerializer> and using the <xref:System.Xml.Serialization.XmlSerializer> and the various attributes of the <xref:System.Xml.Serialization> namespace.</span></span>

- <span data-ttu-id="e06ef-124"><xref:System.Xml.Serialization.XmlSerializer> a atributy <xref:System.Xml.Serialization> obor názvů jsou navržené tak, aby bylo možné mapovat typy rozhraní .NET Framework na libovolný platný typ definovaný ve schématu XML a tak poskytovat velmi přesnou kontrolu nad zastoupení typu ve formátu XML.</span><span class="sxs-lookup"><span data-stu-id="e06ef-124">The <xref:System.Xml.Serialization.XmlSerializer> and the attributes of the <xref:System.Xml.Serialization> namespace are designed to allow you to map .NET Framework types to any valid type defined in XML Schema, and so they provide for very precise control over how a type is represented in XML.</span></span> <span data-ttu-id="e06ef-125"><xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.DataContractAttribute> a <xref:System.Runtime.Serialization.DataMemberAttribute> poskytují velmi málo kontrolu nad zastoupení typu ve formátu XML.</span><span class="sxs-lookup"><span data-stu-id="e06ef-125">The <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> provide very little control over how a type is represented in XML.</span></span> <span data-ttu-id="e06ef-126">Můžete nastavit jenom obory názvů a názvů používaných ke znázornění typu a jeho pole nebo vlastnosti v souboru XML a pořadí, ve kterém polí a vlastností zobrazí v kódu XML:</span><span class="sxs-lookup"><span data-stu-id="e06ef-126">You can only specify the namespaces and names used to represent the type and its fields or properties in the XML, and the sequence in which the fields and properties appear in the XML:</span></span>

    ```csharp
    [DataContract(
    Namespace="urn:Contoso:2006:January:29",
    Name="LineItem")]
    public class LineItem
    {
         [DataMember(Name="ItemNumber",IsRequired=true,Order=0)]
         public string itemNumber;
         [DataMember(Name="Quantity",IsRequired=false,Order = 1)]
         public decimal quantity;
         [DataMember(Name="Price",IsRequired=false,Order = 2)]
         public decimal unitPrice;
    }
    ```

    <span data-ttu-id="e06ef-127">Všechno ostatní o struktuře XML, který představuje typ formátu .NET je určeno <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="e06ef-127">Everything else about the structure of the XML used to represent the .NET type is determined by the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>

- <span data-ttu-id="e06ef-128">Tím, že není velkou kontrolu nad jak je typem a nelze je reprezentovat ve formátu XML, stane vysoce předvídatelné pro procesu serializace <xref:System.Runtime.Serialization.DataContractSerializer>a tím usnadňuje optimalizaci.</span><span class="sxs-lookup"><span data-stu-id="e06ef-128">By not permitting much control over how a type is to be represented in XML, the serialization process becomes highly predictable for the <xref:System.Runtime.Serialization.DataContractSerializer>, and, thereby, easier to optimize.</span></span> <span data-ttu-id="e06ef-129">Praktické výhodou návrh <xref:System.Runtime.Serialization.DataContractSerializer> je lepší výkon, přibližně deset procent lepší výkon.</span><span class="sxs-lookup"><span data-stu-id="e06ef-129">A practical benefit of the design of the <xref:System.Runtime.Serialization.DataContractSerializer> is better performance, approximately ten percent better performance.</span></span>

- <span data-ttu-id="e06ef-130">Atributy pro použití se službou <xref:System.Xml.Serialization.XmlSerializer> nevyplývá, pole nebo vlastnosti typu se serializovat do formátu XML, zatímco <xref:System.Runtime.Serialization.DataMemberAttribute> pro použití se službou <xref:System.Runtime.Serialization.DataContractSerializer> ukazuje explicitně pole nebo vlastnosti serializují.</span><span class="sxs-lookup"><span data-stu-id="e06ef-130">The attributes for use with the <xref:System.Xml.Serialization.XmlSerializer> do not indicate which fields or properties of the type are serialized into XML, whereas the <xref:System.Runtime.Serialization.DataMemberAttribute> for use with the <xref:System.Runtime.Serialization.DataContractSerializer> shows explicitly which fields or properties are serialized.</span></span> <span data-ttu-id="e06ef-131">Kontrakty dat jsou proto explicitní smluv o struktuře dat, která aplikace je odesílat a přijímat.</span><span class="sxs-lookup"><span data-stu-id="e06ef-131">Therefore, data contracts are explicit contracts about the structure of the data that an application is to send and receive.</span></span>

- <span data-ttu-id="e06ef-132"><xref:System.Xml.Serialization.XmlSerializer> Může překládat pouze veřejné členy objektu rozhraní .NET do formátu XML, <xref:System.Runtime.Serialization.DataContractSerializer> přeložit jako objekty její členové objektů do souboru XML bez ohledu na to modifikátory přístupu těchto členů.</span><span class="sxs-lookup"><span data-stu-id="e06ef-132">The <xref:System.Xml.Serialization.XmlSerializer> can only translate the public members of a .NET object into XML, the <xref:System.Runtime.Serialization.DataContractSerializer> can translate the members of objects into XML regardless of the access modifiers of those members.</span></span>

- <span data-ttu-id="e06ef-133">Následkem schopnost serializovat neveřejným členům typů do souboru XML, <xref:System.Runtime.Serialization.DataContractSerializer> má méně omezení pro různé typy .NET, které mohou serializovat do formátu XML.</span><span class="sxs-lookup"><span data-stu-id="e06ef-133">As a consequence of being able to serialize the non-public members of types into XML, the <xref:System.Runtime.Serialization.DataContractSerializer> has fewer restrictions on the variety of .NET types that it can serialize into XML.</span></span> <span data-ttu-id="e06ef-134">Zejména může překládat na typy XML jako <xref:System.Collections.Hashtable> , které implementují <xref:System.Collections.IDictionary> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e06ef-134">In particular, it can translate into XML types like <xref:System.Collections.Hashtable> that implement the <xref:System.Collections.IDictionary> interface.</span></span> <span data-ttu-id="e06ef-135"><xref:System.Runtime.Serialization.DataContractSerializer> Je mnohem pravděpodobnější lze serializovat instance všechny existující typ formátu .NET do formátu XML bez nutnosti změňte definici typu nebo vyvíjet obálku pro něj.</span><span class="sxs-lookup"><span data-stu-id="e06ef-135">The <xref:System.Runtime.Serialization.DataContractSerializer> is much more likely to be able to serialize the instances of any pre-existing .NET type into XML without having to either modify the definition of the type or develop a wrapper for it.</span></span>

- <span data-ttu-id="e06ef-136">Jiné důsledkem <xref:System.Runtime.Serialization.DataContractSerializer> nebudete mít přístup k neveřejným členům typu je, že vyžaduje úplný vztah důvěryhodnosti, že <xref:System.Xml.Serialization.XmlSerializer> nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="e06ef-136">Another consequence of the <xref:System.Runtime.Serialization.DataContractSerializer> being able to access the non-public members of a type is that it requires full trust, whereas the <xref:System.Xml.Serialization.XmlSerializer> does not.</span></span> <span data-ttu-id="e06ef-137">Přístupová oprávnění plné důvěryhodnosti kódu poskytuje úplný přístup ke všem prostředkům na počítači, který je přístupný pomocí přihlašovacích údajů, za kterých je kód spuštěn.</span><span class="sxs-lookup"><span data-stu-id="e06ef-137">The Full Trust code access permission gives complete access to all resources on a machine that can be accessed using the credentials under which the code is executing.</span></span> <span data-ttu-id="e06ef-138">Tato možnost by měla sloužit opatrně plně důvěryhodný kód přistupuje k všechny prostředky ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="e06ef-138">This option should be used with care as fully trusted code accesses all resources on your machine.</span></span>

- <span data-ttu-id="e06ef-139"><xref:System.Runtime.Serialization.DataContractSerializer> Zahrnuje některé podpory pro správu verzí:</span><span class="sxs-lookup"><span data-stu-id="e06ef-139">The <xref:System.Runtime.Serialization.DataContractSerializer> incorporates some support for versioning:</span></span>

    - <span data-ttu-id="e06ef-140"><xref:System.Runtime.Serialization.DataMemberAttribute> Má <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> vlastnost, která je možné přiřadit hodnotu false pro členy, které jsou přidány do nové verze kontraktu dat, které nebyly k dispozici v dřívějších verzích, a tím umožní aplikace s touto novou verzí smlouvy bude nelze zpracovat starší verze.</span><span class="sxs-lookup"><span data-stu-id="e06ef-140">The <xref:System.Runtime.Serialization.DataMemberAttribute> has an <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> property that can be assigned a value of false for members that are added to new versions of a data contract that were not present in earlier versions, thereby allowing applications with the newer version of the contract to be able to process earlier versions.</span></span>

    - <span data-ttu-id="e06ef-141">Tím, že implementace kontraktu dat <xref:System.Runtime.Serialization.IExtensibleDataObject> rozhraní, jeden můžete povolit <xref:System.Runtime.Serialization.DataContractSerializer> předat členy definované v novějších verzích kontraktu dat prostřednictvím aplikací s předchozími verzemi smlouvy.</span><span class="sxs-lookup"><span data-stu-id="e06ef-141">By having a data contract implement the <xref:System.Runtime.Serialization.IExtensibleDataObject> interface, one can allow the <xref:System.Runtime.Serialization.DataContractSerializer> to pass members defined in newer versions of a data contract through applications with earlier versions of the contract.</span></span>

<span data-ttu-id="e06ef-142">Bez ohledu na některé rozdíly, XML, do kterého <xref:System.Xml.Serialization.XmlSerializer> serializuje typu ve výchozím nastavení je sémanticky shodná s XML, do kterého <xref:System.Runtime.Serialization.DataContractSerializer> serializuje typu podle oboru názvů XML není výslovně uveden.</span><span class="sxs-lookup"><span data-stu-id="e06ef-142">Despite all of the differences, the XML into which the <xref:System.Xml.Serialization.XmlSerializer> serializes a type by default is semantically identical to the XML into which the <xref:System.Runtime.Serialization.DataContractSerializer> serializes a type, provided the namespace for the XML is explicitly defined.</span></span> <span data-ttu-id="e06ef-143">Následující třídy, která má atributy pro použití s nástrojem serializátory, je přeložit na sémanticky identické XML pomocí <xref:System.Xml.Serialization.XmlSerializer> a <xref:System.Runtime.Serialization.DataContractAttribute>:</span><span class="sxs-lookup"><span data-stu-id="e06ef-143">The following class, which has attributes for use with both of the serializers, is translated into semantically identical XML by the <xref:System.Xml.Serialization.XmlSerializer> and by the <xref:System.Runtime.Serialization.DataContractAttribute>:</span></span>

```csharp
[Serializable]
[XmlRoot(Namespace="urn:Contoso:2006:January:29")]
[DataContract(Namespace="urn:Contoso:2006:January:29")]
public class LineItem
{
     [DataMember]
     public string ItemNumber;
     [DataMember]
     public decimal Quantity;
     [DataMember]
     public decimal UnitPrice;
}
```

<span data-ttu-id="e06ef-144">Sady Windows software development kit (SDK) zahrnuje nástroj příkazového řádku, volá se, [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="e06ef-144">The Windows software development kit (SDK) includes a command-line tool called the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="e06ef-145">Nástroj xsd.exe použitý s webovými službami ASP.NET, jako jsou Svcutil.exe lze generovat definice datových typů .NET ze schématu XML.</span><span class="sxs-lookup"><span data-stu-id="e06ef-145">Like the xsd.exe tool used with ASP.NET Web services, Svcutil.exe can generate definitions of .NET data types from XML Schema.</span></span> <span data-ttu-id="e06ef-146">Pokud jsou tyto typy kontraktů dat <xref:System.Runtime.Serialization.DataContractSerializer> může vysílat XML ve formátu definovaná pomocí schématu XML; v opačném případě jsou určeny pro použití serializace <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="e06ef-146">The types are data contracts if the <xref:System.Runtime.Serialization.DataContractSerializer> can emit XML in the format defined by the XML Schema; otherwise, they are intended for serialization using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="e06ef-147">Svcutil.exe lze také generování schématu XML z kontraktů dat pomocí jeho `dataContractOnly` přepnout.</span><span class="sxs-lookup"><span data-stu-id="e06ef-147">Svcutil.exe can also generate an XML schema from data contracts by using its `dataContractOnly` switch.</span></span>

> [!NOTE]
> <span data-ttu-id="e06ef-148">I když webových služeb ASP.NET použijte <xref:System.Xml.Serialization.XmlSerializer>a režim kompatibility WCF ASP.NET umožňuje služby WCF, které napodobují chování webových služeb ASP.NET, ASP.NET možnost kompatibility neomezuje z nich se má používat <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="e06ef-148">Although ASP.NET Web services use the <xref:System.Xml.Serialization.XmlSerializer>, and WCF ASP.NET compatibility mode makes WCF services mimic the behavior of ASP.NET Web services, the ASP.NET compatibility option does not restrict one to using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="e06ef-149">Stále můžete použít <xref:System.Runtime.Serialization.DataContractSerializer> pomocí služby spuštěné v režimu kompatibility ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="e06ef-149">One can still use the <xref:System.Runtime.Serialization.DataContractSerializer> with services running in the ASP.NET compatibility mode.</span></span>

## <a name="service-development"></a><span data-ttu-id="e06ef-150">Vývoj služby</span><span class="sxs-lookup"><span data-stu-id="e06ef-150">Service Development</span></span>

<span data-ttu-id="e06ef-151">Pro vývoj služby pomocí ASP.NET, bylo běžné přidáte <xref:System.Web.Services.WebService> atribut třídy a <xref:System.Web.Services.WebMethodAttribute> k některé z metod této třídy, které mají být operace služby:</span><span class="sxs-lookup"><span data-stu-id="e06ef-151">To develop a service using ASP.NET, it has been customary to add the <xref:System.Web.Services.WebService> attribute to a class, and the <xref:System.Web.Services.WebMethodAttribute> to any of that class’ methods that are to be operations of the service:</span></span>

```csharp
[WebService]
public class Service : T:System.Web.Services.WebService
{
    [WebMethod]
    public string Echo(string input)
    {
       return input;
    }
}
```

<span data-ttu-id="e06ef-152">ASP.NET 2.0 zavedla možnost přidání atributu <xref:System.Web.Services.WebService> a <xref:System.Web.Services.WebMethodAttribute> rozhraní, nikoli třída a zápis třídu pro implementaci rozhraní:</span><span class="sxs-lookup"><span data-stu-id="e06ef-152">ASP.NET 2.0 introduced the option of adding the attribute <xref:System.Web.Services.WebService> and <xref:System.Web.Services.WebMethodAttribute> to an interface rather than to a class, and writing a class to implement the interface:</span></span>

```csharp
[WebService]
public interface IEcho
{
    [WebMethod]
    string Echo(string input);
}

public class Service : IEcho
{

   public string Echo(string input)
   {
        return input;
    }
}
```

<span data-ttu-id="e06ef-153">Pomocí této možnosti má být upřednostňované, protože rozhraní s <xref:System.Web.Services.WebService> atributu tvoří kontrakt operace prováděné na službu, kterou lze opětovně použít s různými třídami, které mohou implementovat tento stejný kontrakt různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="e06ef-153">Using this option is to be preferred, because the interface with the <xref:System.Web.Services.WebService> attribute constitutes a contract for the operations performed by the service that can be reused with various classes that might implement that same contract in different ways.</span></span>

<span data-ttu-id="e06ef-154">WCF service se poskytuje tak, že definujete jeden nebo více koncových bodů WCF.</span><span class="sxs-lookup"><span data-stu-id="e06ef-154">A WCF service is provided by defining one or more WCF endpoints.</span></span> <span data-ttu-id="e06ef-155">Koncový bod je definován tak, že adresa, vazba a kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="e06ef-155">An endpoint is defined by an address, a binding and a service contract.</span></span> <span data-ttu-id="e06ef-156">Adresa definuje, ve kterém se služba nachází.</span><span class="sxs-lookup"><span data-stu-id="e06ef-156">The address defines where the service is located.</span></span> <span data-ttu-id="e06ef-157">Vazba Určuje, jak komunikovat se službou.</span><span class="sxs-lookup"><span data-stu-id="e06ef-157">The binding specifies how to communicate with the service.</span></span> <span data-ttu-id="e06ef-158">Kontrakt služby definuje operace, které služby mohou provádět.</span><span class="sxs-lookup"><span data-stu-id="e06ef-158">The service contract defines the operations that the service can perform.</span></span>

<span data-ttu-id="e06ef-159">Kontrakt služby je obvykle definován jako první, tak, že přidáte <xref:System.ServiceModel.ServiceContractAttribute> a <xref:System.ServiceModel.OperationContractAttribute> rozhraní:</span><span class="sxs-lookup"><span data-stu-id="e06ef-159">The service contract is usually defined first, by adding <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> to an interface:</span></span>

```csharp
[ServiceContract]
public interface IEcho
{
     [OperationContract]
     string Echo(string input);
}
```

<span data-ttu-id="e06ef-160"><xref:System.ServiceModel.ServiceContractAttribute> Určuje, že rozhraní definuje kontrakt služby WCF a <xref:System.ServiceModel.OperationContractAttribute> označuje, která, pokud existuje, metod rozhraní definuje operace kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="e06ef-160">The <xref:System.ServiceModel.ServiceContractAttribute> specifies that the interface defines a WCF service contract, and the <xref:System.ServiceModel.OperationContractAttribute> indicates which, if any, of the methods of the interface define operations of the service contract.</span></span>

<span data-ttu-id="e06ef-161">Po definování kontraktu služby je implementována ve třídě, tím, že třída implementovat rozhraní, ve které je definováno kontraktu služby:</span><span class="sxs-lookup"><span data-stu-id="e06ef-161">Once a service contract has been defined, it is implemented in a class, by having the class implement the interface by which the service contract is defined:</span></span>

```csharp
public class Service : IEcho
{
    public string Echo(string input)
    {
       return input;
    }
}
```

<span data-ttu-id="e06ef-162">Třídu, která implementuje kontrakt služby se označuje jako služba typu ve službě WCF.</span><span class="sxs-lookup"><span data-stu-id="e06ef-162">A class that implements a service contract is referred to as a service type in WCF.</span></span>

<span data-ttu-id="e06ef-163">Dalším krokem je spojit adresu a vazbu s typem služby.</span><span class="sxs-lookup"><span data-stu-id="e06ef-163">The next step is to associate an address and a binding with a service type.</span></span> <span data-ttu-id="e06ef-164">Který se obvykle provádí v konfiguračním souboru, tak, že upravíte soubor přímo nebo pomocí editoru konfigurace s použitím technologie WCF k dispozici.</span><span class="sxs-lookup"><span data-stu-id="e06ef-164">That is typically done in a configuration file, either by editing the file directly, or by using a configuration editor provided with WCF.</span></span> <span data-ttu-id="e06ef-165">Tady je příklad konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="e06ef-165">Here is an example of a configuration file.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
     <system.serviceModel>
      <services>
      <service name="Service ">
       <endpoint
        address="EchoService"
        binding="basicHttpBinding"
        contract="IEchoService "/>
      </service>
      </services>
     </system.serviceModel>
</configuration>
```

<span data-ttu-id="e06ef-166">Vazba určuje sadu protokolů pro komunikaci s aplikací.</span><span class="sxs-lookup"><span data-stu-id="e06ef-166">The binding specifies the set of protocols for communicating with the application.</span></span> <span data-ttu-id="e06ef-167">V následující tabulce jsou uvedeny vazeb poskytovaných systémem, které představují běžné možnosti.</span><span class="sxs-lookup"><span data-stu-id="e06ef-167">The following table lists the system-provided bindings that represent common options.</span></span>

|<span data-ttu-id="e06ef-168">Název</span><span class="sxs-lookup"><span data-stu-id="e06ef-168">Name</span></span>|<span data-ttu-id="e06ef-169">Účel</span><span class="sxs-lookup"><span data-stu-id="e06ef-169">Purpose</span></span>|
|----------|-------------|
|<span data-ttu-id="e06ef-170">BasicHttpBinding</span><span class="sxs-lookup"><span data-stu-id="e06ef-170">BasicHttpBinding</span></span>|<span data-ttu-id="e06ef-171">Interoperabilita s Web services a klienti podporující WS-BasicProfile 1.1 a 1.0 profil základní zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e06ef-171">Interoperability with Web services and clients supporting the WS-BasicProfile 1.1 and Basic Security Profile 1.0.</span></span>|
|<span data-ttu-id="e06ef-172">WSHttpBinding</span><span class="sxs-lookup"><span data-stu-id="e06ef-172">WSHttpBinding</span></span>|<span data-ttu-id="e06ef-173">Interoperabilita s Web services a klienti podporující WS-\* protokolů přes protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="e06ef-173">Interoperability with Web services and clients that support the WS-\* protocols over HTTP.</span></span>|
|<span data-ttu-id="e06ef-174">WSDualHttpBinding</span><span class="sxs-lookup"><span data-stu-id="e06ef-174">WSDualHttpBinding</span></span>|<span data-ttu-id="e06ef-175">Duplexní komunikaci pomocí protokolu HTTP, podle kterého příjemce původní zprávu neodpovídejte přímo do počáteční odesílatele, ale může přenést libovolný počet odpovědí po určitou dobu pomocí protokolu HTTP v souladu s WS-\* protokoly.</span><span class="sxs-lookup"><span data-stu-id="e06ef-175">Duplex HTTP communication, by which the receiver of an initial message does not reply directly to the initial sender, but may transmit any number of responses over a period of time by using HTTP in conformity with WS-\* protocols.</span></span>|
|<span data-ttu-id="e06ef-176">WSFederationBinding</span><span class="sxs-lookup"><span data-stu-id="e06ef-176">WSFederationBinding</span></span>|<span data-ttu-id="e06ef-177">Komunikaci pomocí protokolu HTTP, ve kterém lze ovládat přístup k prostředkům služby na základě přihlašovacích údajů vydané poskytovatele přihlašovacích údajů explicitně identifikovat.</span><span class="sxs-lookup"><span data-stu-id="e06ef-177">HTTP communication, in which access to the resources of a service can be controlled based on credentials issued by an explicitly-identified credential provider.</span></span>|
|<span data-ttu-id="e06ef-178">NetTcpBinding</span><span class="sxs-lookup"><span data-stu-id="e06ef-178">NetTcpBinding</span></span>|<span data-ttu-id="e06ef-179">Bezpečné, spolehlivé a vysoce výkonné komunikace mezi entitami softwaru WCF přes síť.</span><span class="sxs-lookup"><span data-stu-id="e06ef-179">Secure, reliable, high-performance communication between WCF software entities across a network.</span></span>|
|<span data-ttu-id="e06ef-180">NetNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="e06ef-180">NetNamedPipeBinding</span></span>|<span data-ttu-id="e06ef-181">Bezpečné, spolehlivé a vysoce výkonné komunikace mezi entitami WCF software ve stejném počítači.</span><span class="sxs-lookup"><span data-stu-id="e06ef-181">Secure, reliable, high-performance communication between WCF software entities on the same machine.</span></span>|
|<span data-ttu-id="e06ef-182">NetMsmqBinding</span><span class="sxs-lookup"><span data-stu-id="e06ef-182">NetMsmqBinding</span></span>|<span data-ttu-id="e06ef-183">Komunikace mezi entitami WCF software pomocí služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="e06ef-183">Communication between WCF software entities by using MSMQ.</span></span>|
|<span data-ttu-id="e06ef-184">MsmqIntegrationBinding</span><span class="sxs-lookup"><span data-stu-id="e06ef-184">MsmqIntegrationBinding</span></span>|<span data-ttu-id="e06ef-185">Komunikace mezi entitou softwaru WCF a jiné entity software pomocí služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="e06ef-185">Communication between a WCF software entity and another software entity by using MSMQ.</span></span>|
|<span data-ttu-id="e06ef-186">NetPeerTcpBinding</span><span class="sxs-lookup"><span data-stu-id="e06ef-186">NetPeerTcpBinding</span></span>|<span data-ttu-id="e06ef-187">Komunikace mezi entitami softwaru WCF pomocí sítě Peer-to-Peer Windows.</span><span class="sxs-lookup"><span data-stu-id="e06ef-187">Communication between WCF software entities by using Windows Peer-to-Peer Networking.</span></span>|

<span data-ttu-id="e06ef-188">Vazeb poskytovaných systémem <xref:System.ServiceModel.BasicHttpBinding>, zahrnuje sadu protokolů podporovaných webových služeb ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="e06ef-188">The system-provided binding, <xref:System.ServiceModel.BasicHttpBinding>, incorporates the set of protocols supported by ASP.NET Web services.</span></span>

<span data-ttu-id="e06ef-189">Vlastní vazby WCF aplikací se snadno definují jako kolekce tříd element vazby, které používá WCF k implementaci jednotlivých protokolů.</span><span class="sxs-lookup"><span data-stu-id="e06ef-189">Custom bindings for WCF applications are easily defined as collections of the binding element classes that WCF uses to implement individual protocols.</span></span> <span data-ttu-id="e06ef-190">Nové prvky vazby je možné zapisovat na představují další protokoly.</span><span class="sxs-lookup"><span data-stu-id="e06ef-190">New binding elements can be written to represent additional protocols.</span></span>

<span data-ttu-id="e06ef-191">Vnitřní chování typů služeb je možné upravit pomocí vlastností rodinu tříd pojmenovanou chování.</span><span class="sxs-lookup"><span data-stu-id="e06ef-191">The internal behavior of service types can be adjusted using the properties of a family of classes called behaviors.</span></span> <span data-ttu-id="e06ef-192">Tady <xref:System.ServiceModel.ServiceBehaviorAttribute> třída se používá k určení, že je typ služby s více vlákny.</span><span class="sxs-lookup"><span data-stu-id="e06ef-192">Here, the <xref:System.ServiceModel.ServiceBehaviorAttribute> class is used to specify that the service type is to be multithreaded.</span></span>

```csharp
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple]
public class DerivativesCalculatorServiceType: IDerivativesCalculator
```

<span data-ttu-id="e06ef-193">Některá chování, jako jsou <xref:System.ServiceModel.ServiceBehaviorAttribute>, jsou atributy.</span><span class="sxs-lookup"><span data-stu-id="e06ef-193">Some behaviors, like <xref:System.ServiceModel.ServiceBehaviorAttribute>, are attributes.</span></span> <span data-ttu-id="e06ef-194">Jiné, ty s vlastnostmi, které byste měli správci nastavit, lze upravit v konfiguraci aplikace.</span><span class="sxs-lookup"><span data-stu-id="e06ef-194">Others, the ones with properties that administrators would want to set, can be modified in the configuration of an application.</span></span>

<span data-ttu-id="e06ef-195">V programovacích typy služeb, často používají tvoří <xref:System.ServiceModel.OperationContext> třídy.</span><span class="sxs-lookup"><span data-stu-id="e06ef-195">In programming service types, frequent use is made of the <xref:System.ServiceModel.OperationContext> class.</span></span> <span data-ttu-id="e06ef-196">Jeho statické <xref:System.ServiceModel.OperationContext.Current%2A> vlastnost poskytuje přístup k informacím o kontextu, ve kterém je spuštěná operace.</span><span class="sxs-lookup"><span data-stu-id="e06ef-196">Its static <xref:System.ServiceModel.OperationContext.Current%2A> property provides access to information about the context in which an operation is running.</span></span> <span data-ttu-id="e06ef-197"><xref:System.ServiceModel.OperationContext> je podobný i <xref:System.Web.HttpContext> a <xref:System.EnterpriseServices.ContextUtil> třídy.</span><span class="sxs-lookup"><span data-stu-id="e06ef-197"><xref:System.ServiceModel.OperationContext> is similar to both the <xref:System.Web.HttpContext> and <xref:System.EnterpriseServices.ContextUtil> classes.</span></span>

## <a name="hosting"></a><span data-ttu-id="e06ef-198">Hostování</span><span class="sxs-lookup"><span data-stu-id="e06ef-198">Hosting</span></span>

<span data-ttu-id="e06ef-199">Webové služby ASP.NET jsou kompilovány do sestavení knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="e06ef-199">ASP.NET Web services are compiled into a class library assembly.</span></span> <span data-ttu-id="e06ef-200">Soubor s názvem souboru definice služby je za předpokladu, že má příponou .asmx a obsahuje `@ WebService` směrnice, identifikující třídu, která obsahuje kód pro službu a sestavení, ve kterém se nachází.</span><span class="sxs-lookup"><span data-stu-id="e06ef-200">A file called the service file is provided that has the extension .asmx and contains an `@ WebService` directive that identifies the class that contains the code for the service and the assembly in which it is located.</span></span>

```
<%@ WebService Language="C#" Class="Service,ServiceAssembly" %>
```

<span data-ttu-id="e06ef-201">Služba soubor je zkopírován do kořenový adresář aplikace ASP.NET v Internetové informační služby (IIS) a sestavení je zkopírován do podadresáři \bin tento kořenový adresář aplikace.</span><span class="sxs-lookup"><span data-stu-id="e06ef-201">The service file is copied into an ASP.NET application root in Internet Information Services (IIS), and the assembly is copied into the \bin subdirectory of that application root.</span></span> <span data-ttu-id="e06ef-202">Aplikace je přístupná pak s použitím adresu uniform resource locator (URL) souboru služby v kořenovém adresáři aplikace.</span><span class="sxs-lookup"><span data-stu-id="e06ef-202">The application is then accessible by using the uniform resource locator (URL) of the service file in the application root.</span></span>

<span data-ttu-id="e06ef-203">V rámci služby IIS 5.1 a 6.0, Windows WAS Process Activation Service (), která je k dispozici jako součást služby IIS 7.0, a v rámci všech aplikací .NET, je možné snadno hostovat služby WCF.</span><span class="sxs-lookup"><span data-stu-id="e06ef-203">WCF services can readily be hosted within IIS 5.1 or 6.0, the Windows Process Activation Service (WAS) that is provided as part of IIS 7.0, and within any .NET application.</span></span> <span data-ttu-id="e06ef-204">K hostování služby ve službě IIS 5.1 a 6.0, musíte použít službu HTTP jako protokol pro přenos komunikace.</span><span class="sxs-lookup"><span data-stu-id="e06ef-204">To host a service in IIS 5.1 or 6.0, the service must use HTTP as the communications transport protocol.</span></span>

<span data-ttu-id="e06ef-205">K hostování služby IIS 5.1, 6.0 nebo v rámci WAS, použijte následující kroky:</span><span class="sxs-lookup"><span data-stu-id="e06ef-205">To host a service within IIS 5.1, 6.0 or within WAS, use the follows steps:</span></span>

1. <span data-ttu-id="e06ef-206">Zkompilujte do sestavení knihovny tříd typ služby.</span><span class="sxs-lookup"><span data-stu-id="e06ef-206">Compile the service type into a class library assembly.</span></span>

2. <span data-ttu-id="e06ef-207">Vytvořte službu soubor s příponou .svc s `@ ServiceHost` směrnice identifikovat typ služby:</span><span class="sxs-lookup"><span data-stu-id="e06ef-207">Create a service file with a .svc extension with an `@ ServiceHost` directive to identify the service type:</span></span>

    ```
    <%@ServiceHost language="c#" Service="MyService" %>
    ```

3. <span data-ttu-id="e06ef-208">Zkopírujte soubor služby do virtuálního adresáře a sestavení, v podadresáři \bin daného virtuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="e06ef-208">Copy the service file into a virtual directory, and the assembly into the \bin subdirectory of that virtual directory.</span></span>

4. <span data-ttu-id="e06ef-209">Zkopírujte konfigurační soubor do virtuálního adresáře a pojmenujte ho souboru Web.config.</span><span class="sxs-lookup"><span data-stu-id="e06ef-209">Copy the configuration file into the virtual directory, and name it Web.config.</span></span>

 <span data-ttu-id="e06ef-210">Aplikace je přístupná pak pomocí adresy URL služby souborů v kořenovém adresáři aplikace.</span><span class="sxs-lookup"><span data-stu-id="e06ef-210">The application is then accessible by using the URL of the service file in the application root.</span></span>

 <span data-ttu-id="e06ef-211">K hostování služby WCF v rámci aplikace .NET, kompilovat typ služby do aplikace odkazuje sestavení knihovny tříd a aplikací na hostitele služby pomocí programu <xref:System.ServiceModel.ServiceHost> třídy.</span><span class="sxs-lookup"><span data-stu-id="e06ef-211">To host a WCF service within a .NET application, compile the service type into a class library assembly referenced by the application, and program the application to host the service using the <xref:System.ServiceModel.ServiceHost> class.</span></span> <span data-ttu-id="e06ef-212">Následuje příklad základní programování vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="e06ef-212">The following is an example of the basic programming required:</span></span>

```csharp
string httpBaseAddress = "http://www.contoso.com:8000/";
string tcpBaseAddress = "net.tcp://www.contoso.com:8080/";

Uri httpBaseAddressUri = new Uri(httpBaseAddress);
Uri tcpBaseAddressUri = new Uri(tcpBaseAddress);

Uri[] baseAddresses = new Uri[] {
 httpBaseAddressUri,
 tcpBaseAddressUri};

using(ServiceHost host = new ServiceHost(
typeof(Service), //"Service" is the name of the service type baseAddresses))
{
     host.Open();

     […] //Wait to receive messages
     host.Close();
}
```

<span data-ttu-id="e06ef-213">Tento příklad ukazuje, jak jsou určené adresy pro jeden nebo více protokolů přenosu v procesu vytváření <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="e06ef-213">This example shows how addresses for one or more transport protocols are specified in the construction of a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="e06ef-214">Tyto adresy jsou označovány jako základní adresy.</span><span class="sxs-lookup"><span data-stu-id="e06ef-214">These addresses are referred to as base addresses.</span></span>

<span data-ttu-id="e06ef-215">Adresa zadaná pro libovolný koncový bod služby WCF je adresa relativní k základní adresa hostitele koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="e06ef-215">The address provided for any endpoint of a WCF service is an address relative to a base address of the endpoint’s host.</span></span> <span data-ttu-id="e06ef-216">Hostitel může mít jednu základní adresu pro každý protokol pro přenos komunikace.</span><span class="sxs-lookup"><span data-stu-id="e06ef-216">The host can have one base address for each communication transport protocol.</span></span> <span data-ttu-id="e06ef-217">V ukázkové konfiguraci v konfiguračním souboru předchozí <xref:System.ServiceModel.BasicHttpBinding> vybrané pro koncový bod používá HTTP jako přenosový protokol, tak adresu koncového bodu, `EchoService`, je relativní vzhledem k základní adresu HTTP hostitele.</span><span class="sxs-lookup"><span data-stu-id="e06ef-217">In the sample configuration in the preceding configuration file, the <xref:System.ServiceModel.BasicHttpBinding> selected for the endpoint uses HTTP as the transport protocol, so the address of the endpoint, `EchoService`, is relative to the host’s HTTP base address.</span></span> <span data-ttu-id="e06ef-218">V případě hostitele v předchozím příkladu je základní adresu HTTP `http://www.contoso.com:8000/`.</span><span class="sxs-lookup"><span data-stu-id="e06ef-218">In the case of the host in the preceding example, the HTTP base address is `http://www.contoso.com:8000/`.</span></span> <span data-ttu-id="e06ef-219">Služby hostované v rámci služby IIS nebo WAS základní adresa je adresa URL služby souboru služby.</span><span class="sxs-lookup"><span data-stu-id="e06ef-219">For a service hosted within IIS or WAS, the base address is the URL of the service’s service file.</span></span>

<span data-ttu-id="e06ef-220">Pouze služby hostované v IIS nebo WAS a které jsou nakonfigurované s protokolem HTTP jako přenosový protokol výhradně, lze použít možnost režim kompatibility WCF ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="e06ef-220">Only services hosted in IIS or WAS, and which are configured with HTTP as the transport protocol exclusively, can be made to use WCF ASP.NET compatibility mode option.</span></span> <span data-ttu-id="e06ef-221">Zapnutí této možnosti vyžaduje následující kroky.</span><span class="sxs-lookup"><span data-stu-id="e06ef-221">Turning that option on requires the following steps.</span></span>

1. <span data-ttu-id="e06ef-222">Musíte přidat programátor <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> atributu pro typ služby a určit, že režim kompatibility ASP.NET je buď povoleno nebo požadováno.</span><span class="sxs-lookup"><span data-stu-id="e06ef-222">The programmer must add the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> attribute to the service type and specify that ASP.NET compatibility mode is either allowed or required.</span></span>

    ```csharp
    [System.ServiceModel.Activation.AspNetCompatibilityRequirements(
          RequirementsMode=AspNetCompatibilityRequirementsMode.Require)]
    public class DerivativesCalculatorServiceType: IDerivativesCalculator
    ```

2. <span data-ttu-id="e06ef-223">Správce musí nakonfigurovat aplikaci, aby používala režim kompatibility ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="e06ef-223">The administrator must configure the application to use the ASP.NET compatibility mode.</span></span>

    ```xml
    <configuration>
         <system.serviceModel>
          <services>
          […]
          </services>
          <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>
        </system.serviceModel>
    </configuration>
    ```

    <span data-ttu-id="e06ef-224">Aplikace WCF je také nakonfigurovat .asmx používat jako rozšíření pro jejich služby souborů a nikoli .svc.</span><span class="sxs-lookup"><span data-stu-id="e06ef-224">WCF applications can also be configured to use .asmx as the extension for their service files rather than .svc.</span></span>

    ```xml
    <system.web>
         <compilation>
          <compilation debug="true">
          <buildProviders>
           <remove extension=".asmx"/>
           <add extension=".asmx"
            type="System.ServiceModel.ServiceBuildProvider,
            System.ServiceModel,
            Version=3.0.0.0,
            Culture=neutral,
            PublicKeyToken=b77a5c561934e089" />
          </buildProviders>
          </compilation>
         </compilation>
    </system.web>
    ```

    <span data-ttu-id="e06ef-225">Tuto možnost můžete uložit z museli upravovat klienty, kteří jsou nakonfigurovány pro použití adresy URL služby souborů .asmx při úpravě službu používat WCF.</span><span class="sxs-lookup"><span data-stu-id="e06ef-225">That option can save you from having to modify clients that are configured to use the URLs of .asmx service files when modifying a service to use WCF.</span></span>

## <a name="client-development"></a><span data-ttu-id="e06ef-226">Vývoj pro klientské</span><span class="sxs-lookup"><span data-stu-id="e06ef-226">Client Development</span></span>

<span data-ttu-id="e06ef-227">Klienti pro webových služeb ASP.NET se generují pomocí nástroje příkazového řádku, WSDL.exe, který obsahuje adresu URL souboru .asmx jako vstup.</span><span class="sxs-lookup"><span data-stu-id="e06ef-227">Clients for ASP.NET Web services are generated using the command-line tool, WSDL.exe, which provides the URL of the .asmx file as input.</span></span> <span data-ttu-id="e06ef-228">Nástroj odpovídající poskytované WCF je [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="e06ef-228">The corresponding tool provided by WCF is [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="e06ef-229">Generuje modul kódu s definicí kontraktu služby a definice třídy klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="e06ef-229">It generates a code module with the definition of the service contract and the definition of a WCF client class.</span></span> <span data-ttu-id="e06ef-230">Také generuje konfigurační soubor s adresou a vazby služby.</span><span class="sxs-lookup"><span data-stu-id="e06ef-230">It also generates a configuration file with the address and binding of the service.</span></span>

<span data-ttu-id="e06ef-231">V programovacích klienta vzdálené služby je obecně vhodné program podle asynchronního zpracování.</span><span class="sxs-lookup"><span data-stu-id="e06ef-231">In programming a client of a remote service it is generally advisable to program according to an asynchronous pattern.</span></span> <span data-ttu-id="e06ef-232">Kód generovaný nástrojem WSDL.exe vždy zajišťující synchronního a asynchronního zpracování ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="e06ef-232">The code generated by the WSDL.exe tool always provides for both a synchronous and an asynchronous pattern by default.</span></span> <span data-ttu-id="e06ef-233">Kód vygenerovaný [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) můžete zadat buď vzor.</span><span class="sxs-lookup"><span data-stu-id="e06ef-233">The code generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) can provide for either pattern.</span></span> <span data-ttu-id="e06ef-234">Ve výchozím nastavení poskytuje pro synchronní vzor.</span><span class="sxs-lookup"><span data-stu-id="e06ef-234">It provides for the synchronous pattern by default.</span></span> <span data-ttu-id="e06ef-235">Pokud je spuštěn nástroj `/async` přepnout, generovaný kód poskytuje pro asynchronní zpracování.</span><span class="sxs-lookup"><span data-stu-id="e06ef-235">If the tool is executed with the `/async` switch, then the generated code provides for the asynchronous pattern.</span></span>

<span data-ttu-id="e06ef-236">Neexistuje žádná záruka, že názvy tříd klienta WCF generovaných ASP. Nástroj WSDL.exe vaší sítě, ve výchozím nastavení, odpovídaly názvům v generované pomocí nástroje Svcutil.exe třídy klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="e06ef-236">There is no guarantee that names in the WCF client classes generated by ASP.NET’s WSDL.exe tool, by default, match the names in WCF client classes generated by the Svcutil.exe tool.</span></span> <span data-ttu-id="e06ef-237">Zejména názvy vlastností třídy, které mají k serializaci pomocí <xref:System.Xml.Serialization.XmlSerializer> ve výchozím nastavení, disponují přípona vlastností v kódu generovaném nástrojem Svcutil.exe, což není případ nástrojem WSDL.exe.</span><span class="sxs-lookup"><span data-stu-id="e06ef-237">In particular, the names of the properties of classes that have to be serialized using the <xref:System.Xml.Serialization.XmlSerializer> are, by default, given the suffix Property in the code generated by the Svcutil.exe tool, which is not the case with the WSDL.exe tool.</span></span>

## <a name="message-representation"></a><span data-ttu-id="e06ef-238">Reprezentace zprávy</span><span class="sxs-lookup"><span data-stu-id="e06ef-238">Message Representation</span></span>

<span data-ttu-id="e06ef-239">Záhlaví SOAP zpráv odesílaných i přijímaných webových služeb ASP.NET se dají přizpůsobit.</span><span class="sxs-lookup"><span data-stu-id="e06ef-239">The headers of the SOAP messages sent and received by ASP.NET Web services can be customized.</span></span> <span data-ttu-id="e06ef-240">Třída je odvozena z <xref:System.Web.Services.Protocols.SoapHeader> pro definici struktury hlavičky a pak <xref:System.Web.Services.Protocols.SoapHeaderAttribute> slouží k určení přítomnosti záhlaví.</span><span class="sxs-lookup"><span data-stu-id="e06ef-240">A class is derived from <xref:System.Web.Services.Protocols.SoapHeader> to define the structure of the header, and then the <xref:System.Web.Services.Protocols.SoapHeaderAttribute> is used to indicate the presence of the header.</span></span>

```csharp
public class SomeProtocol : SoapHeader
{
     public long CurrentValue;
     public long Total;
}

[WebService]
public interface IEcho
{
     SomeProtocol ProtocolHeader
     {
      get;
     set;
     }

     [WebMethod]
     [SoapHeader("ProtocolHeader")]
     string PlaceOrders(PurchaseOrderType order);
}

public class Service: WebService, IEcho
{
     private SomeProtocol protocolHeader;

     public SomeProtocol ProtocolHeader
     {
         get
         {
              return this.protocolHeader;
         }

         set
         {
              this.protocolHeader = value;
         }
     }

     string PlaceOrders(PurchaseOrderType order)
     {
         long currentValue = this.protocolHeader.CurrentValue;
     }
}
```

<span data-ttu-id="e06ef-241">WCF obsahuje atributy, <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute>, a <xref:System.ServiceModel.MessageBodyMemberAttribute> k popisu struktury protokolu SOAP zprávy odeslané a přijaté službou.</span><span class="sxs-lookup"><span data-stu-id="e06ef-241">The WCF provides the attributes, <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute>, and <xref:System.ServiceModel.MessageBodyMemberAttribute> to describe the structure of the SOAP messages sent and received by a service.</span></span>

```csharp
[DataContract]
public class SomeProtocol
{
     [DataMember]
     public long CurrentValue;
     [DataMember]
     public long Total;
}

[DataContract]
public class Item
{
     [DataMember]
     public string ItemNumber;
     [DataMember]
     public decimal Quantity;
     [DataMember]
     public decimal UnitPrice;
}

[MessageContract]
public class ItemMessage
{
     [MessageHeader]
     public SomeProtocol ProtocolHeader;
     [MessageBody]
     public Item Content;
}

[ServiceContract]
public interface IItemService
{
     [OperationContract]
     public void DeliverItem(ItemMessage itemMessage);
}
```

<span data-ttu-id="e06ef-242">Tato syntaxe poskytuje reprezentaci explicitní konstrukce zprávy, že struktura zpráv, které je zahrnuto v kódu webové služby technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="e06ef-242">This syntax yields an explicit representation of the structure of the messages, whereas the structure of messages is implied by the code of an ASP.NET Web service.</span></span> <span data-ttu-id="e06ef-243">Také v syntaxi ASP.NET záhlaví zpráv jsou reprezentovány jako vlastnosti služby, například `ProtocolHeader` vlastnost v předchozím příkladu, zatímco ve WCF syntaxe jsou přesněji reprezentována jako vlastnosti zprávy.</span><span class="sxs-lookup"><span data-stu-id="e06ef-243">Also, in the ASP.NET syntax, message headers are represented as properties of the service, such as the `ProtocolHeader` property in the previous example, whereas in WCF syntax, they are more accurately represented as properties of messages.</span></span> <span data-ttu-id="e06ef-244">Navíc WCF umožňuje záhlaví zpráv, které mají být přidány do konfigurace koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="e06ef-244">Also, WCF allows message headers to be added to the configuration of endpoints.</span></span>

```xml
<service name="Service ">
     <endpoint
      address="EchoService"
      binding="basicHttpBinding"
      contract="IEchoService ">
      <headers>
      <dsig:X509Certificate
       xmlns:dsig="http://www.w3.org/2000/09/xmldsig#">
       ...
      </dsig:X509Certificate>
      </headers>
     </endpoint>
</service>
```

<span data-ttu-id="e06ef-245">Možnost umožňuje vyhnout se všechny odkazy na záhlaví infrastruktury protokolu v kódu klienta nebo služby: záhlaví jsou přidány do zprávy z důvodu konfigurace koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="e06ef-245">That option allows you to avoid any reference to infrastructural protocol headers in the code for a client or service: the headers are added to messages because of how the endpoint is configured.</span></span>

## <a name="service-description"></a><span data-ttu-id="e06ef-246">Popis služby</span><span class="sxs-lookup"><span data-stu-id="e06ef-246">Service Description</span></span>

<span data-ttu-id="e06ef-247">Vydání požadavku HTTP GET pro soubor .asmx technologie ASP.NET webové služby s dotazem WSDL způsobí, že technologie ASP.NET generuje WSDL k popisu služby.</span><span class="sxs-lookup"><span data-stu-id="e06ef-247">Issuing an HTTP GET request for the .asmx file of an ASP.NET Web service with the query WSDL causes ASP.NET to generate WSDL to describe the service.</span></span> <span data-ttu-id="e06ef-248">Vrátí, na který WSDL jako odpověď na požadavek.</span><span class="sxs-lookup"><span data-stu-id="e06ef-248">It returns that WSDL as the response to the request.</span></span>

<span data-ttu-id="e06ef-249">ASP.NET 2.0 možné ověřit, že je kompatibilní s Basic Profile 1.1 organizace Interoperability služby webové služby (WS-I) a pro vložení deklarace identity, že služba je kompatibilní s do své WSDL.</span><span class="sxs-lookup"><span data-stu-id="e06ef-249">ASP.NET 2.0 made it possible to validate that a service is compliant with the Basic Profile 1.1 of the Web Services-Interoperability Organization (WS-I), and to insert a claim that the service is compliant into its WSDL.</span></span> <span data-ttu-id="e06ef-250">To znamená dokončeno pomocí `ConformsTo` a `EmitConformanceClaims` parametry <xref:System.Web.Services.WebServiceBindingAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="e06ef-250">That is done using the `ConformsTo` and `EmitConformanceClaims` parameters of the <xref:System.Web.Services.WebServiceBindingAttribute> attribute.</span></span>

```csharp
[WebService(Namespace = "http://tempuri.org/")]
[WebServiceBinding(
     ConformsTo = WsiProfiles.BasicProfile1_1,
     EmitConformanceClaims=true)]
public interface IEcho
```

<span data-ttu-id="e06ef-251">WSDL, který ASP.NET generuje pro službu se dají přizpůsobit.</span><span class="sxs-lookup"><span data-stu-id="e06ef-251">The WSDL that ASP.NET generates for a service can be customized.</span></span> <span data-ttu-id="e06ef-252">Přizpůsobení probíhají vytvořením odvozené třídy z <xref:System.Web.Services.Description.ServiceDescriptionFormatExtension> přidání položek do jazyka WSDL.</span><span class="sxs-lookup"><span data-stu-id="e06ef-252">Customizations are made by creating a derived class of <xref:System.Web.Services.Description.ServiceDescriptionFormatExtension> to add items to the WSDL.</span></span>

<span data-ttu-id="e06ef-253">Vydání požadavku HTTP GET s dotazem WSDL souboru .svc služby WCF se nehostují ve službě IIS 51 koncový bod HTTP, 6.0 nebo WAS způsobí, že odpoví WSDL k popisu služby WCF.</span><span class="sxs-lookup"><span data-stu-id="e06ef-253">Issuing an HTTP GET request with the query WSDL for the .svc file of a WCF service with an HTTP endpoint hosted within IIS 51, 6.0 or WAS causes WCF to respond with WSDL to describe the service.</span></span> <span data-ttu-id="e06ef-254">Vydání požadavku HTTP GET s dotazem WSDL na základní adresu HTTP služby hostované v rámci aplikace .NET má stejný účinek, pokud httpGetEnabled je nastavena na hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="e06ef-254">Issuing an HTTP GET request with the query WSDL to the HTTP base address of a service hosted within a .NET application has the same effect if httpGetEnabled is set to true.</span></span>

<span data-ttu-id="e06ef-255">WCF se však také reaguje na požadavky WS-MetadataExchange WSDL, který generuje k popisu služby.</span><span class="sxs-lookup"><span data-stu-id="e06ef-255">However, WCF also responds to WS-MetadataExchange requests with WSDL that it generates to describe a service.</span></span> <span data-ttu-id="e06ef-256">Webové služby ASP.NET nemají integrovanou podporu pro WS-MetadataExchange požadavky.</span><span class="sxs-lookup"><span data-stu-id="e06ef-256">ASP.NET Web services do not have built-in support for WS-MetadataExchange requests.</span></span>

<span data-ttu-id="e06ef-257">WSDL, který generuje WCF je možné výrazně přizpůsobit.</span><span class="sxs-lookup"><span data-stu-id="e06ef-257">The WSDL that WCF generates can be extensively customized.</span></span> <span data-ttu-id="e06ef-258"><xref:System.ServiceModel.Description.ServiceMetadataBehavior> Třída poskytuje některé funkce pro přizpůsobení jazyka WSDL.</span><span class="sxs-lookup"><span data-stu-id="e06ef-258">The <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class provides some facilities for customizing the WSDL.</span></span> <span data-ttu-id="e06ef-259">WCF je možné nakonfigurovat také negeneruje WSDL, ale závisí na použití statický soubor WSDL na dané adrese URL.</span><span class="sxs-lookup"><span data-stu-id="e06ef-259">The WCF can also be configured to not generate WSDL, but rather to use a static WSDL file at a given URL.</span></span>

```xml
<behaviors>
     <behavior name="DescriptionBehavior">
     <metadataPublishing
      enableMetadataExchange="true"
      enableGetWsdl="true"
      enableHelpPage="true"
      metadataLocation=
      "http://localhost/DerivativesCalculatorService/Service.WSDL"/>
     </behavior>
</behaviors>
```

## <a name="exception-handling"></a><span data-ttu-id="e06ef-260">Zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="e06ef-260">Exception Handling</span></span>

<span data-ttu-id="e06ef-261">V rozhraní ASP.NET Web services jsou vráceny neošetřené výjimky klientům jako chyb SOAP.</span><span class="sxs-lookup"><span data-stu-id="e06ef-261">In ASP.NET Web services, unhandled exceptions are returned to clients as SOAP faults.</span></span> <span data-ttu-id="e06ef-262">Můžete také explicitně vyvolat instance <xref:System.Web.Services.Protocols.SoapException> třídy a mít větší kontrolu nad obsahem chybu protokolu SOAP, který získá přenést do klienta.</span><span class="sxs-lookup"><span data-stu-id="e06ef-262">You can also explicitly throw instances of the <xref:System.Web.Services.Protocols.SoapException> class and have more control over the content of the SOAP fault that gets transmitted to the client.</span></span>

<span data-ttu-id="e06ef-263">Ve službách WCF nevrací neošetřené výjimky klientům jako chyb SOAP, aby se zabránilo neúmyslnému vystavení prostřednictvím výjimky citlivé informace.</span><span class="sxs-lookup"><span data-stu-id="e06ef-263">In WCF services, unhandled exceptions are not returned to clients as SOAP faults to prevent sensitive information being inadvertently exposed through the exceptions.</span></span> <span data-ttu-id="e06ef-264">Konfigurace nastavení je dostupné na mají neošetřené výjimky vracené klientům pro účely ladění.</span><span class="sxs-lookup"><span data-stu-id="e06ef-264">A configuration setting is provided to have unhandled exceptions returned to clients for the purpose of debugging.</span></span>

<span data-ttu-id="e06ef-265">Pokud chcete vrátit chyby SOAP pro klienty, můžete vyvolat instance obecného typu <xref:System.ServiceModel.FaultException%601>s použitím kontraktu dat typu, Obecné.</span><span class="sxs-lookup"><span data-stu-id="e06ef-265">To return SOAP faults to clients, you can throw instances of the generic type, <xref:System.ServiceModel.FaultException%601>, using the data contract type as the generic type.</span></span> <span data-ttu-id="e06ef-266">Můžete také přidat <xref:System.ServiceModel.FaultContractAttribute> atributy pro operace k určení chyb, které operace mohou zobrazit.</span><span class="sxs-lookup"><span data-stu-id="e06ef-266">You can also add <xref:System.ServiceModel.FaultContractAttribute> attributes to operations to specify the faults that an operation might yield.</span></span>

```csharp
[DataContract]
public class MathFault
{
     [DataMember]
     public string operation;
     [DataMember]
     public string problemType;
}

[ServiceContract]
public interface ICalculator
{
     [OperationContract]
     [FaultContract(typeof(MathFault))]
     int Divide(int n1, int n2);
}
```

<span data-ttu-id="e06ef-267">Proto za následek chyby je to možné, inzerované v jazyce WSDL pro službu, umožňuje tak klientským programátorům předvídat chyb, které můžete výsledkem operace a zápisu že odpovídající catch – příkazy.</span><span class="sxs-lookup"><span data-stu-id="e06ef-267">Doing so results in the possible faults being advertised in the WSDL for the service, allowing client programmers to anticipate which faults can result from an operation, and write the appropriate catch statements.</span></span>

```csharp
try
{
     result = client.Divide(value1, value2);
}
catch (FaultException<MathFault> e)
{
 Console.WriteLine("FaultException<MathFault>: Math fault while doing "
  + e.Detail.operation
  + ". Problem: "
  + e.Detail.problemType);
}
```

## <a name="state-management"></a><span data-ttu-id="e06ef-268">Správa stavu</span><span class="sxs-lookup"><span data-stu-id="e06ef-268">State Management</span></span>

<span data-ttu-id="e06ef-269">Třída používaný k implementaci technologie ASP.NET webové služby může být odvozena z <xref:System.Web.Services.WebService>.</span><span class="sxs-lookup"><span data-stu-id="e06ef-269">The class used to implement an ASP.NET Web service may be derived from <xref:System.Web.Services.WebService>.</span></span>

```csharp
public class Service : WebService, IEcho
{

 public string Echo(string input)
 {
  return input;
 }
}
```

<span data-ttu-id="e06ef-270">V takovém případě mohou být naprogramovány třídu použít <xref:System.Web.Services.WebService> základní třídy vlastnost kontextu pro přístup k <xref:System.Web.HttpContext> objektu.</span><span class="sxs-lookup"><span data-stu-id="e06ef-270">In that case, the class can be programmed to use the <xref:System.Web.Services.WebService> base class’ Context property to access a <xref:System.Web.HttpContext> object.</span></span> <span data-ttu-id="e06ef-271"><xref:System.Web.HttpContext> Objektu lze použít k aktualizaci a získat informace o stavu aplikace pomocí vlastností aplikace a slouží k aktualizaci a načtení informací o stavu relace pomocí její vlastnosti relace.</span><span class="sxs-lookup"><span data-stu-id="e06ef-271">The <xref:System.Web.HttpContext> object can be used to update and retrieve application state information by using its Application property, and can be used to update and retrieve session state information by using its Session property.</span></span>

<span data-ttu-id="e06ef-272">Technologie ASP.NET poskytuje významnou kontrolu nad kde informace, které jsou přístupné pomocí vlastnosti relace stavu relace <xref:System.Web.HttpContext> skutečně uložená.</span><span class="sxs-lookup"><span data-stu-id="e06ef-272">ASP.NET provides considerable control over where the session state information accessed by using the Session property of the <xref:System.Web.HttpContext> is actually stored.</span></span> <span data-ttu-id="e06ef-273">Mohou být uložena v souborech cookie, databázi, do paměti jako aktuální server nebo paměti určený server.</span><span class="sxs-lookup"><span data-stu-id="e06ef-273">It may be stored in cookies, in a database, in the memory of the current server, or in the memory of a designated server.</span></span> <span data-ttu-id="e06ef-274">Volba se provádí v konfiguračním souboru služby.</span><span class="sxs-lookup"><span data-stu-id="e06ef-274">The choice is made in the service’s configuration file.</span></span>

<span data-ttu-id="e06ef-275">WCF poskytuje rozšiřitelné objekty pro správu stavu.</span><span class="sxs-lookup"><span data-stu-id="e06ef-275">The WCF provides extensible objects for state management.</span></span> <span data-ttu-id="e06ef-276">Rozšiřitelné objekty jsou objekty, které implementují <xref:System.ServiceModel.IExtensibleObject%601>.</span><span class="sxs-lookup"><span data-stu-id="e06ef-276">Extensible objects are objects that implement <xref:System.ServiceModel.IExtensibleObject%601>.</span></span> <span data-ttu-id="e06ef-277">Nejdůležitější rozšiřitelné objekty jsou <xref:System.ServiceModel.ServiceHostBase> a <xref:System.ServiceModel.InstanceContext>.</span><span class="sxs-lookup"><span data-stu-id="e06ef-277">The most important extensible objects are <xref:System.ServiceModel.ServiceHostBase> and <xref:System.ServiceModel.InstanceContext>.</span></span> <span data-ttu-id="e06ef-278">`ServiceHostBase` umožňuje udržovat stav všech instancí služby typy na stejném hostiteli přístup, zatímco `InstanceContext` umožňuje zachovat stav, který je přístupný libovolnému kódu v rámci stejné instance daného typu služby.</span><span class="sxs-lookup"><span data-stu-id="e06ef-278">`ServiceHostBase` allows you to maintain state that all of the instances of all of the service types on the same host can access, while `InstanceContext` allows you to maintain state that can be accessed by any code running within the same instance of a service type.</span></span>

<span data-ttu-id="e06ef-279">Tady, typ služby `TradingSystem`, má <xref:System.ServiceModel.ServiceBehaviorAttribute> , která určuje, že všechna volání ze stejné instance klienta WCF se směrují do stejné instance daného typu služby.</span><span class="sxs-lookup"><span data-stu-id="e06ef-279">Here, the service type, `TradingSystem`, has a <xref:System.ServiceModel.ServiceBehaviorAttribute> that specifies that all calls from the same WCF client instance are routed to the same instance of the service type.</span></span>

```csharp
[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerSession)]
public class TradingSystem: ITradingService
```

<span data-ttu-id="e06ef-280">Třída, `DealData`, definuje stav, který je přístupný libovolnému kódu ve stejné instanci daného typu služby s.</span><span class="sxs-lookup"><span data-stu-id="e06ef-280">The class, `DealData`, defines state that can be accessed by any code running in the same instance of a service type.</span></span>

```csharp
internal class DealData: IExtension<InstanceContext>
{
 public string DealIdentifier = null;
 public Trade[] Trades = null;
}
```

<span data-ttu-id="e06ef-281">V kódu, který implementuje jedné z operací kontraktu služby, typ služby `DealData` stav objektu se přidá do stavu aktuální instance daného typu služby.</span><span class="sxs-lookup"><span data-stu-id="e06ef-281">In the code of the service type that implements one of the operations of the service contract, a `DealData` state object is added to the state of the current instance of the service type.</span></span>

```csharp
string ITradingService.BeginDeal()
{
 string dealIdentifier = Guid.NewGuid().ToString();
 DealData state = new DealData(dealIdentifier);
 OperationContext.Current.InstanceContext.Extensions.Add(state);
 return dealIdentifier;
}
```

<span data-ttu-id="e06ef-282">Tento objekt stavu jde pak načíst a upravovat kód, který implementuje jiné operace kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="e06ef-282">That state object can then be retrieved and modified by the code that implements another of the service contract’s operations.</span></span>

```csharp
void ITradingService.AddTrade(Trade trade)
{
 DealData dealData =  OperationContext.Current.InstanceContext.Extensions.Find<DealData>();
 dealData.AddTrade(trade);
}
```

<span data-ttu-id="e06ef-283">Informace v stavu kde že technologie ASP.NET poskytuje ovládací prvek průběhu <xref:System.Web.HttpContext> třída je ve skutečnosti uložena, WCF, alespoň v jeho počáteční verze poskytuje žádnou kontrolu nad tím, kde jsou uložená rozšiřitelné objekty.</span><span class="sxs-lookup"><span data-stu-id="e06ef-283">Whereas ASP.NET provides control over where state information in the <xref:System.Web.HttpContext> class is actually stored, WCF, at least in its initial version, provides no control over where extensible objects are stored.</span></span> <span data-ttu-id="e06ef-284">Který představuje nejlepších důvod pro výběr režim kompatibility ASP.NET pro služby WCF.</span><span class="sxs-lookup"><span data-stu-id="e06ef-284">That constitutes the very best reason for selecting the ASP.NET compatibility mode for a WCF service.</span></span> <span data-ttu-id="e06ef-285">Pokud je nutné konfigurovat stav správy, pak vyžadují pro režim kompatibility ASP.NET umožňuje použít zařízení <xref:System.Web.HttpContext> třídy přesně tak, jak se používají v technologii ASP.NET a taky nakonfigurovat kde informace stavu společností <xref:System.Web.HttpContext> třída je uložena.</span><span class="sxs-lookup"><span data-stu-id="e06ef-285">If configurable state management is imperative, then opting for the ASP.NET compatibility mode allows you to use the facilities of the <xref:System.Web.HttpContext> class exactly as they are used in ASP.NET, and also to configure where state information managed by using the <xref:System.Web.HttpContext> class is stored.</span></span>

## <a name="security"></a><span data-ttu-id="e06ef-286">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="e06ef-286">Security</span></span>

<span data-ttu-id="e06ef-287">Možnosti pro zabezpečení webové služby jsou pro zabezpečení všechny aplikace služby IIS.</span><span class="sxs-lookup"><span data-stu-id="e06ef-287">The options for securing ASP.NET Web services are those for securing any IIS application.</span></span> <span data-ttu-id="e06ef-288">Protože aplikace WCF je možné hostovat nejen v rámci služby IIS, ale také v rámci žádného spustitelného souboru, .NET, možnosti pro zabezpečení aplikací WCF se musí provádět nezávisle na zařízení služby IIS.</span><span class="sxs-lookup"><span data-stu-id="e06ef-288">Because WCF applications can be hosted not only within IIS but also within any .NET executable, the options for securing WCF applications must be made independent from the facilities of IIS.</span></span> <span data-ttu-id="e06ef-289">Zařízení k dispozici pro webové služby ASP.NET jsou ale také k dispozici pro spuštění v režimu kompatibility ASP.NET služby WCF.</span><span class="sxs-lookup"><span data-stu-id="e06ef-289">However, the facilities provided for ASP.NET Web services are also available for WCF services running in ASP.NET compatibility mode.</span></span>

### <a name="security-authentication"></a><span data-ttu-id="e06ef-290">Zabezpečení: Ověřování</span><span class="sxs-lookup"><span data-stu-id="e06ef-290">Security: Authentication</span></span>

<span data-ttu-id="e06ef-291">Služba IIS poskytuje funkce pro řízení přístupu k aplikacím, které můžete vybrat anonymní přístup nebo různé režimy ověřování: Ověřování Windows, ověřování hodnotou hash, základní ověřování a ověřování pomocí služby .NET Passport.</span><span class="sxs-lookup"><span data-stu-id="e06ef-291">IIS provides facilities for controlling access to applications by which you can select either anonymous access or a variety of modes of authentication: Windows Authentication, Digest Authentication, Basic Authentication, and .NET Passport Authentication.</span></span> <span data-ttu-id="e06ef-292">Možnost ověřování Windows lze použít k řízení přístupu k webové služby ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="e06ef-292">The Windows Authentication option can be used to control access to ASP.NET Web services.</span></span> <span data-ttu-id="e06ef-293">Když jsou aplikací služby WCF hostované v rámci služby IIS, služba IIS musí nakonfigurovat tak, aby povolovala anonymní přístup k aplikaci, tak, že ověřování je možné spravovat pomocí WCF, který podporuje ověřování Windows z různých dalších možností.</span><span class="sxs-lookup"><span data-stu-id="e06ef-293">However, when WCF applications are hosted within IIS, IIS must be configured to permit anonymous access to the application, so that authentication can be managed by WCF itself, which does support Windows authentication among various other options.</span></span> <span data-ttu-id="e06ef-294">Další možnosti, které jsou integrované zahrnovat uživatelské jméno tokenů, certifikáty X.509, tokeny SAML a služba CardSpace karty, ale je také možné definovat vlastní ověřovací mechanismy.</span><span class="sxs-lookup"><span data-stu-id="e06ef-294">The other options that are built-in include username tokens, X.509 certificates, SAML tokens, and CardSpace card, but custom authentication mechanisms can also be defined.</span></span>

### <a name="security-impersonation"></a><span data-ttu-id="e06ef-295">Zabezpečení: Zosobnění</span><span class="sxs-lookup"><span data-stu-id="e06ef-295">Security: Impersonation</span></span>

<span data-ttu-id="e06ef-296">Technologie ASP.NET poskytuje identity element pomocí technologie ASP.NET webové služby můžete provést zosobnění s určitým uživatelem nebo přihlašovacích údajů uživatele podle toho, která jsou součástí aktuálního požadavku.</span><span class="sxs-lookup"><span data-stu-id="e06ef-296">ASP.NET provides an identity element by which an ASP.NET Web service can be made to impersonate a particular user or whichever user’s credentials are provided with the current request.</span></span> <span data-ttu-id="e06ef-297">Tento element lze použít ke konfiguraci zosobnění v WCF aplikace běžící v režimu kompatibility ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="e06ef-297">That element can be used to configure impersonation in WCF applications running in ASP.NET compatibility mode.</span></span>

<span data-ttu-id="e06ef-298">Určování určitého uživatele k zosobnění, poskytuje tento systém konfigurace WCF vlastní element identity.</span><span class="sxs-lookup"><span data-stu-id="e06ef-298">The WCF configuration system provides its own identity element for designating a particular user to impersonate.</span></span> <span data-ttu-id="e06ef-299">Také klienti WCF a služeb můžete nezávisle na sobě nakonfigurovat pro zosobnění.</span><span class="sxs-lookup"><span data-stu-id="e06ef-299">Also, WCF clients and services can be independently configured for impersonation.</span></span> <span data-ttu-id="e06ef-300">Klienty můžete nakonfigurovat zosobnit aktuálního uživatele, když odesílají žádosti.</span><span class="sxs-lookup"><span data-stu-id="e06ef-300">Clients can be configured to impersonate the current user when they transmit requests.</span></span>

```xml
<behaviors>
     <behavior name="DerivativesCalculatorClientBehavior">
      <clientCredentials>
      <windows allowedImpersonationLevel="Impersonation"/>
      </clientCredentials>
     </behavior>
</behaviors>
```

<span data-ttu-id="e06ef-301">Operace služby je možné nakonfigurovat k zosobnění přihlašovacích údajů uživatele podle toho, která jsou součástí aktuálního požadavku.</span><span class="sxs-lookup"><span data-stu-id="e06ef-301">Service operations can be configured to impersonate whichever user’s credentials are provided with the current request.</span></span>

```csharp
[OperationBehavior(Impersonation = ImpersonationOption.Required)]
public void Receive(Message input)
```

### <a name="security-authorization-using-access-control-lists"></a><span data-ttu-id="e06ef-302">Zabezpečení: Autorizace pomocí seznamů řízení přístupu</span><span class="sxs-lookup"><span data-stu-id="e06ef-302">Security: Authorization using Access Control Lists</span></span>

<span data-ttu-id="e06ef-303">Seznamy řízení přístupu (ACL) slouží k omezení přístupu k souborům .asmx.</span><span class="sxs-lookup"><span data-stu-id="e06ef-303">Access Control Lists (ACLs) can be used to restrict access to .asmx files.</span></span> <span data-ttu-id="e06ef-304">Seznamy ACL na hledání souborů .svc WCF se ignorují však s výjimkou v režim kompatibility ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="e06ef-304">However, ACLs on WCF .svc files are ignored except in ASP.NET compatibility mode.</span></span>

### <a name="security-role-based-authorization"></a><span data-ttu-id="e06ef-305">Zabezpečení: Autorizace na základě rolí</span><span class="sxs-lookup"><span data-stu-id="e06ef-305">Security: Role-based Authorization</span></span>

<span data-ttu-id="e06ef-306">Možnost ověřování Windows služby IIS můžete použít ve spojení s elementem autorizace k dispozici v jazyce ASP.NET konfigurace usnadňuje ověřování na základě rolí pro webové služby ASP.NET na základě skupin Windows, ke kterým uživatelé jsou přiřazení .</span><span class="sxs-lookup"><span data-stu-id="e06ef-306">The IIS Windows Authentication option can be used in conjunction with the authorization element provided by the ASP.NET configuration language to facilitate role-based authorization for ASP.NET Web services based on the Windows groups to which users are assigned.</span></span> <span data-ttu-id="e06ef-307">ASP.NET 2.0 zavedené obecnější mechanismus ověřování na základě role: role zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="e06ef-307">ASP.NET 2.0 introduced a more general role-based authorization mechanism: role providers.</span></span>

<span data-ttu-id="e06ef-308">Zprostředkovatele rolí jsou třídy, že všechny základní rozhraní pro dotazující o rolích, které je uživatel přiřazenou implementovat, ale každý zprostředkovatele rolí ví, jak načítal příslušné informace z jiného zdroje.</span><span class="sxs-lookup"><span data-stu-id="e06ef-308">Role providers are classes that all implement a basic interface for enquiring about the roles to which a user is assigned, but each role provider knows how to retrieve that information from a different source.</span></span> <span data-ttu-id="e06ef-309">ASP.NET 2.0 obsahuje role poskytovatele, který lze načíst přiřazení rolí z databáze Microsoft SQL Server a další, které můžete načíst přiřazení role ze Správce autorizací systému Windows Server 2003.</span><span class="sxs-lookup"><span data-stu-id="e06ef-309">ASP.NET 2.0 provides a role provider that can retrieve role assignments from a Microsoft SQL Server database, and another that can retrieve role assignments from the Windows Server 2003 Authorization Manager.</span></span>

<span data-ttu-id="e06ef-310">Mechanismus poskytovatele role lze použít ve skutečnosti bez ohledu na jejich technologie ASP.NET v jakékoli aplikaci .NET, včetně aplikace WCF.</span><span class="sxs-lookup"><span data-stu-id="e06ef-310">The role provider mechanism can actually be used independently of ASP.NET in any .NET application, including a WCF application.</span></span> <span data-ttu-id="e06ef-311">Následující ukázková konfigurace pro aplikace WCF ukazuje, jak pomocí poskytovatele rolí prostředí ASP.NET je možnost vybraná prostřednictvím <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.</span><span class="sxs-lookup"><span data-stu-id="e06ef-311">The following sample configuration for a WCF application shows how the use of an ASP.NET role provider is an option selected by means of the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.</span></span>

```xml
<system.serviceModel>
     <services>
         <service name="Service.ResourceAccessServiceType"
             behaviorConfiguration="ServiceBehavior">
             <endpoint
              address="ResourceAccessService"
              binding="wsHttpBinding"
              contract="Service.IResourceAccessContract"/>
         </service>
     </services>
     <behaviors>
       <behavior name="ServiceBehavior">
       <serviceAuthorization principalPermissionMode="UseAspNetRoles"/>
      </behavior>
     </behaviors>
</system.serviceModel>
```

### <a name="security-claims-based-authorization"></a><span data-ttu-id="e06ef-312">Zabezpečení: Autorizace na základě rolí</span><span class="sxs-lookup"><span data-stu-id="e06ef-312">Security: Claims-based Authorization</span></span>

<span data-ttu-id="e06ef-313">Jeden z vašich nejdůležitějších inovace služby WCF je důkladná podpora pro autorizaci přístupu k chráněným prostředkům na základě deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="e06ef-313">One of the most important innovations of WCF is its thorough support for authorizing access to protected resources based on claims.</span></span> <span data-ttu-id="e06ef-314">Deklarace identity se skládají typu, práva a hodnotu, licence ovladače, třeba.</span><span class="sxs-lookup"><span data-stu-id="e06ef-314">Claims consist of a type, a right and a value, a drivers’ license, for example.</span></span> <span data-ttu-id="e06ef-315">Je sada deklarací o nosiče, z nichž jeden je držitele datum narození.</span><span class="sxs-lookup"><span data-stu-id="e06ef-315">It makes a set of claims about the bearer, one of which is the bearer’s date of birth.</span></span> <span data-ttu-id="e06ef-316">Typ této deklarace identity je datum narození, když hodnota deklarace identity je datum narození ovladače.</span><span class="sxs-lookup"><span data-stu-id="e06ef-316">The type of that claim is date of birth, while the value of the claim is the driver’s birth date.</span></span> <span data-ttu-id="e06ef-317">Pravé straně, který uděluje deklaraci identity nositele Určuje, co můžete dělat nositele hodnotou deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="e06ef-317">The right that a claim confers on the bearer specifies what the bearer can do with the claim’s value.</span></span> <span data-ttu-id="e06ef-318">V případě deklarace identity ovladače datum narození vpravo je vlastníkem: ovladač disponuje, datum narození ale nelze, například, ji změnit.</span><span class="sxs-lookup"><span data-stu-id="e06ef-318">In the case of the claim of the driver’s date of birth, the right is possession: the driver possesses that date of birth but cannot, for example, alter it.</span></span> <span data-ttu-id="e06ef-319">Autorizace na základě rolí obklopuje autorizace na základě role, protože role jsou typu deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="e06ef-319">Claims-based authorization encloses role-based authorization, because roles are a type of claim.</span></span>

<span data-ttu-id="e06ef-320">Autorizace na základě deklarací identity provádí porovnání sadu deklarací identity pro požadavky na přístup, operace a v závislosti na výsledku této porovnání, udělujete nebo odepíráte přístup k operaci.</span><span class="sxs-lookup"><span data-stu-id="e06ef-320">Authorization based on claims is accomplished by comparing a set of claims to the access requirements of the operation and, depending on the outcome of that comparison, granting or denying access to the operation.</span></span> <span data-ttu-id="e06ef-321">Ve službě WCF, můžete určit třídu se použije ke spuštění autorizace na základě rolí, znovu tak, že přiřadíte hodnotu, která `ServiceAuthorizationManager` vlastnost <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.</span><span class="sxs-lookup"><span data-stu-id="e06ef-321">In WCF, you can specify a class to use to run claims-based authorization, once again by assigning a value to the `ServiceAuthorizationManager` property of <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.</span></span>

```xml
<behaviors>
     <behavior name='ServiceBehavior'>
     <serviceAuthorization
     serviceAuthorizationManagerType=
                   'Service.AccessChecker, Service' />
     </behavior>
</behaviors>
```

<span data-ttu-id="e06ef-322">Třídy používané pro spuštění ověřování na základě deklarace identity musí být odvozen z <xref:System.ServiceModel.ServiceAuthorizationManager>, který má pouze jednu metodu pro přepsání, `AccessCheck()`.</span><span class="sxs-lookup"><span data-stu-id="e06ef-322">Classes used to run claims-based authorization must derive from <xref:System.ServiceModel.ServiceAuthorizationManager>, which has just one method to override, `AccessCheck()`.</span></span> <span data-ttu-id="e06ef-323">WCF volá tuto metodu pokaždé, když se operace služby, je vyvolána a poskytuje <xref:System.ServiceModel.OperationContext> objektu, který má deklarace pro uživatele v jeho `ServiceSecurityContext.AuthorizationContext` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e06ef-323">WCF calls that method whenever an operation of the service is invoked and provides a <xref:System.ServiceModel.OperationContext> object, which has the claims for the user in its `ServiceSecurityContext.AuthorizationContext` property.</span></span> <span data-ttu-id="e06ef-324">WCF provádí kompletace deklarace identity o uživateli z libovolné tokenu zabezpečení uživatele pro ověřování, které zůstanou k dispozici úkolu vyhodnocení, jestli tyto deklarace identit postačovat pro příslušná operace.</span><span class="sxs-lookup"><span data-stu-id="e06ef-324">WCF does the work of assembling claims about the user from whatever security token the user provided for authentication, which leaves the of task of evaluating whether those claims suffice for the operation in question.</span></span>

<span data-ttu-id="e06ef-325">WCF automaticky sestaví deklarace identity z nejrůznějších typů zabezpečení token je vysoce důležité inovace, protože je kód pro ověření na základě deklarací zcela nezávislé mechanismu ověřování.</span><span class="sxs-lookup"><span data-stu-id="e06ef-325">That WCF automatically assembles claims from any kind of security token is a highly significant innovation, because it makes the code for authorization based on the claims entirely independent of the authentication mechanism.</span></span> <span data-ttu-id="e06ef-326">Naopak autorizace pomocí seznamů řízení přístupu nebo role v technologii ASP.NET je úzce vázané na ověřování Windows.</span><span class="sxs-lookup"><span data-stu-id="e06ef-326">By contrast, authorization using ACLs or roles in ASP.NET is closely tied to Windows authentication.</span></span>

### <a name="security-confidentiality"></a><span data-ttu-id="e06ef-327">Zabezpečení: Důvěrnost</span><span class="sxs-lookup"><span data-stu-id="e06ef-327">Security: Confidentiality</span></span>

<span data-ttu-id="e06ef-328">Důvěrnost zpráv s webovými službami ASP.NET, které si vyměňují lze zajistit na úrovni přenosu tím, že nakonfigurujete aplikaci v rámci služby IIS, aby používala zabezpečený protokol HTTPS (Hypertext Transfer).</span><span class="sxs-lookup"><span data-stu-id="e06ef-328">The confidentiality of messages exchanged with ASP.NET Web services can be ensured at the transport level by configuring the application within IIS to use the Secure Hypertext Transfer Protocol (HTTPS).</span></span> <span data-ttu-id="e06ef-329">Totéž lze provést aplikací služby WCF hostované v rámci služby IIS.</span><span class="sxs-lookup"><span data-stu-id="e06ef-329">The same can be done for WCF applications hosted within IIS.</span></span> <span data-ttu-id="e06ef-330">Aplikace WCF hostované mimo službu IIS však lze také nastavit pomocí zabezpečeného přenosu protokolu.</span><span class="sxs-lookup"><span data-stu-id="e06ef-330">However, WCF applications hosted outside of IIS can also be configured to use a secure transport protocol.</span></span> <span data-ttu-id="e06ef-331">Důležitější, WCF aplikace lze také nakonfigurovat pro zabezpečení zpráv předtím, než se přenášejí, pomocí protokolu WS-Security.</span><span class="sxs-lookup"><span data-stu-id="e06ef-331">More important, WCF applications can also be configured to secure the messages before they are transported, using the WS-Security protocol.</span></span> <span data-ttu-id="e06ef-332">Zabezpečení tělo zprávy pomocí WS-Security umožňuje přenášet důvěrně napříč prostředníci před dosažením konečného cíle.</span><span class="sxs-lookup"><span data-stu-id="e06ef-332">Securing just the body of a message using WS-Security allows it to be transmitted confidentially across intermediaries before reaching its final destination.</span></span>

## <a name="globalization"></a><span data-ttu-id="e06ef-333">Globalizace</span><span class="sxs-lookup"><span data-stu-id="e06ef-333">Globalization</span></span>

<span data-ttu-id="e06ef-334">Konfigurace jazyka ASP.NET můžete zadat jazykovou verzi pro jednotlivé služby.</span><span class="sxs-lookup"><span data-stu-id="e06ef-334">The ASP.NET configuration language allows you to specify the culture for individual services.</span></span> <span data-ttu-id="e06ef-335">WCF nepodporuje toto nastavení konfigurace s výjimkou v režim kompatibility ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="e06ef-335">The WCF does not support that configuration setting except in ASP.NET compatibility mode.</span></span> <span data-ttu-id="e06ef-336">Chcete-li lokalizovat služby WCF, která nepoužívá režim kompatibility ASP.NET, kompilaci typ služby do sestavení specifické pro jazykovou verzi a mít samostatné koncové body specifické pro jazykovou verzi pro každé sestavení specifické pro jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="e06ef-336">To localize a WCF service that does not use ASP.NET compatibility mode, compile the service type into culture-specific assemblies, and have separate culture-specific endpoints for each culture-specific assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="e06ef-337">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e06ef-337">See also</span></span>

- [<span data-ttu-id="e06ef-338">Porovnání webových služeb ASP.NET se službou WCF na základě účelu a používaných standardů</span><span class="sxs-lookup"><span data-stu-id="e06ef-338">Comparing ASP.NET Web Services to WCF Based on Purpose and Standards Used</span></span>](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used.md)
