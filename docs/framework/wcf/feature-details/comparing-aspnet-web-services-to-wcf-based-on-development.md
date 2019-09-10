---
title: Porovnání webových služeb ASP.NET Web Services s technologií WCF z hlediska vývojových požadavků
ms.date: 03/30/2017
ms.assetid: f362d00e-ce82-484f-9d4f-27e579d5c320
ms.openlocfilehash: 607d0eaabde4e00c1a00b995356bb6d4e1a39234
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855755"
---
# <a name="comparing-aspnet-web-services-to-wcf-based-on-development"></a><span data-ttu-id="d54d7-102">Porovnání webových služeb ASP.NET Web Services s technologií WCF z hlediska vývojových požadavků</span><span class="sxs-lookup"><span data-stu-id="d54d7-102">Comparing ASP.NET Web Services to WCF Based on Development</span></span>

<span data-ttu-id="d54d7-103">Windows Communication Foundation (WCF) má možnost režimu kompatibility ASP.NET, která umožňuje programové použití aplikací WCF a jejich konfiguraci, jako jsou webové služby ASP.NET, a napodobuje jejich chování.</span><span class="sxs-lookup"><span data-stu-id="d54d7-103">Windows Communication Foundation (WCF) has an ASP.NET compatibility mode option to enable WCF applications to be programmed and configured like ASP.NET Web services, and mimic their behavior.</span></span> <span data-ttu-id="d54d7-104">V následujících částech jsou porovnávány webové služby ASP.NET a WCF na základě toho, co je potřeba pro vývoj aplikací pomocí obou technologií.</span><span class="sxs-lookup"><span data-stu-id="d54d7-104">The following sections compare ASP.NET Web services and WCF based on what is required to develop applications using both technologies.</span></span>

## <a name="data-representation"></a><span data-ttu-id="d54d7-105">Reprezentace dat</span><span class="sxs-lookup"><span data-stu-id="d54d7-105">Data Representation</span></span>

<span data-ttu-id="d54d7-106">Vývoj webové služby pomocí ASP.NET obvykle začíná definováním jakýchkoli složitých datových typů, které služba používá.</span><span class="sxs-lookup"><span data-stu-id="d54d7-106">The development of a Web service with ASP.NET typically begins with defining any complex data types the service is to use.</span></span> <span data-ttu-id="d54d7-107">ASP.NET spoléhá na rozhraní <xref:System.Xml.Serialization.XmlSerializer> , aby přeložilo data reprezentovaná .NET Framework typy do XML pro přenos do nebo ze služby a k překladu dat přijatých jako XML do objektů .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d54d7-107">ASP.NET relies on the <xref:System.Xml.Serialization.XmlSerializer> to translate data represented by .NET Framework types to XML for transmission to or from a service and to translate data received as XML into .NET Framework objects.</span></span> <span data-ttu-id="d54d7-108">Definování komplexních datových typů, které musí služba ASP.NET použít, vyžaduje definici .NET Framework třídy, které <xref:System.Xml.Serialization.XmlSerializer> může serializovat a z XML.</span><span class="sxs-lookup"><span data-stu-id="d54d7-108">Defining the complex data types that an ASP.NET service is to use requires the definition of .NET Framework classes that the <xref:System.Xml.Serialization.XmlSerializer> can serialize to and from XML.</span></span> <span data-ttu-id="d54d7-109">Takové třídy lze zapsat ručně nebo vygenerovat z definic typů ve schématu XML pomocí nástroje příkazového řádku XML Schemas/data types support Utility, XSD. exe.</span><span class="sxs-lookup"><span data-stu-id="d54d7-109">Such classes can be written manually, or generated from definitions of the types in XML Schema using the command-line XML Schemas/Data Types Support Utility, xsd.exe.</span></span>

<span data-ttu-id="d54d7-110">Následuje seznam klíčových problémů, které je potřeba znát při definování .NET Framework tříd, které <xref:System.Xml.Serialization.XmlSerializer> může serializovat do a z XML:</span><span class="sxs-lookup"><span data-stu-id="d54d7-110">The following is a list of key issues to know when defining .NET Framework classes that the <xref:System.Xml.Serialization.XmlSerializer> can serialize to and from XML:</span></span>

- <span data-ttu-id="d54d7-111">Pouze veřejná pole a vlastnosti objektů .NET Framework jsou přeloženy do XML.</span><span class="sxs-lookup"><span data-stu-id="d54d7-111">Only the public fields and properties of .NET Framework objects are translated into XML.</span></span>

- <span data-ttu-id="d54d7-112">Instance tříd kolekcí mohou být serializovány do XML pouze v případě, že třídy <xref:System.Collections.IEnumerable> implementují <xref:System.Collections.ICollection> rozhraní nebo.</span><span class="sxs-lookup"><span data-stu-id="d54d7-112">Instances of collection classes can be serialized into XML only if the classes implement either the <xref:System.Collections.IEnumerable> or <xref:System.Collections.ICollection> interface.</span></span>

- <span data-ttu-id="d54d7-113">Třídy, které implementují <xref:System.Collections.IDictionary> rozhraní, <xref:System.Collections.Hashtable>například, se nedají serializovat do XML.</span><span class="sxs-lookup"><span data-stu-id="d54d7-113">Classes that implement the <xref:System.Collections.IDictionary> interface, such as <xref:System.Collections.Hashtable>, cannot be serialized into XML.</span></span>

- <span data-ttu-id="d54d7-114">Skvělé množství typů atributů v <xref:System.Xml.Serialization> oboru názvů lze přidat do .NET Framework třídy a jejích členů pro řízení, jak jsou instance třídy zastoupeny v XML.</span><span class="sxs-lookup"><span data-stu-id="d54d7-114">The great many attribute types in the <xref:System.Xml.Serialization> namespace can be added to a .NET Framework class and its members to control how instances of the class are represented in XML.</span></span>

<span data-ttu-id="d54d7-115">Vývoj aplikací WCF obvykle začíná také definicí komplexních typů.</span><span class="sxs-lookup"><span data-stu-id="d54d7-115">WCF application development usually also begins with the definition of complex types.</span></span> <span data-ttu-id="d54d7-116">WCF je možné použít pro použití stejných typů .NET Framework jako ASP.NET webové služby.</span><span class="sxs-lookup"><span data-stu-id="d54d7-116">WCF can be made to use the same .NET Framework types as ASP.NET Web services.</span></span>

<span data-ttu-id="d54d7-117">WCF<xref:System.Runtime.Serialization.DataContractAttribute> a<xref:System.Runtime.Serialization.DataMemberAttribute> lze jej přidat do .NET Framework typů pro indikaci, že instance typu mají být serializovány do XML a které konkrétní pole nebo vlastnosti tohoto typu mají být serializovány, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="d54d7-117">The WCF<xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> can be added to .NET Framework types to indicate that instances of the type are to be serialized into XML, and which particular fields or properties of the type are to be serialized, as shown in the following sample code.</span></span>

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

<span data-ttu-id="d54d7-118">To znamená, že nula nebo více polí nebo vlastností typu musí být serializován, <xref:System.Runtime.Serialization.DataMemberAttribute> zatímco vlastnost označuje, že konkrétní pole nebo vlastnost má být serializována. <xref:System.Runtime.Serialization.DataContractAttribute></span><span class="sxs-lookup"><span data-stu-id="d54d7-118">The <xref:System.Runtime.Serialization.DataContractAttribute> signifies that zero or more of a type’s fields or properties are to be serialized, while the <xref:System.Runtime.Serialization.DataMemberAttribute> indicates that a particular field or property is to be serialized.</span></span> <span data-ttu-id="d54d7-119"><xref:System.Runtime.Serialization.DataContractAttribute> Lze použít pro třídu nebo strukturu.</span><span class="sxs-lookup"><span data-stu-id="d54d7-119">The <xref:System.Runtime.Serialization.DataContractAttribute> can be applied to a class or structure.</span></span> <span data-ttu-id="d54d7-120"><xref:System.Runtime.Serialization.DataMemberAttribute> Lze použít na pole nebo vlastnost a pole a vlastnosti, na které je atribut použit, mohou být buď veřejné, nebo soukromé.</span><span class="sxs-lookup"><span data-stu-id="d54d7-120">The <xref:System.Runtime.Serialization.DataMemberAttribute> can be applied to a field or a property, and the fields and properties to which the attribute is applied can be either public or private.</span></span> <span data-ttu-id="d54d7-121">Instance typů, které mají <xref:System.Runtime.Serialization.DataContractAttribute> použitou, jsou v rámci WCF označovány jako kontrakty dat.</span><span class="sxs-lookup"><span data-stu-id="d54d7-121">Instances of types that have the <xref:System.Runtime.Serialization.DataContractAttribute> applied to them are referred to as data contracts in WCF.</span></span> <span data-ttu-id="d54d7-122">Jsou serializovány do XML pomocí <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="d54d7-122">They are serialized into XML using <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>

<span data-ttu-id="d54d7-123">Následuje seznam důležitých rozdílů mezi použitím <xref:System.Runtime.Serialization.DataContractSerializer> a <xref:System.Xml.Serialization.XmlSerializer> pomocí a různých atributů <xref:System.Xml.Serialization> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="d54d7-123">The following is a list of the important differences between using the <xref:System.Runtime.Serialization.DataContractSerializer> and using the <xref:System.Xml.Serialization.XmlSerializer> and the various attributes of the <xref:System.Xml.Serialization> namespace.</span></span>

- <span data-ttu-id="d54d7-124"><xref:System.Xml.Serialization.XmlSerializer> A atributy<xref:System.Xml.Serialization> oboru názvů jsou navrženy tak, aby vám umožnily namapovat .NET Framework typy na libovolný platný typ definovaný ve schématu XML, a tak, aby poskytovaly velmi přesnou kontrolu nad tím, jak je typ reprezentován v XML.</span><span class="sxs-lookup"><span data-stu-id="d54d7-124">The <xref:System.Xml.Serialization.XmlSerializer> and the attributes of the <xref:System.Xml.Serialization> namespace are designed to allow you to map .NET Framework types to any valid type defined in XML Schema, and so they provide for very precise control over how a type is represented in XML.</span></span> <span data-ttu-id="d54d7-125"><xref:System.Runtime.Serialization.DataContractAttribute> A <xref:System.Runtime.Serialization.DataContractSerializer> poskytujevelmimaloukontrolunadtím,jakjetypreprezentovánvXML.<xref:System.Runtime.Serialization.DataMemberAttribute></span><span class="sxs-lookup"><span data-stu-id="d54d7-125">The <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> provide very little control over how a type is represented in XML.</span></span> <span data-ttu-id="d54d7-126">Můžete zadat pouze obory názvů a názvy používané pro reprezentaci typu a jeho polí nebo vlastností v XML a pořadí, ve kterém se pole a vlastnosti zobrazí v souboru XML:</span><span class="sxs-lookup"><span data-stu-id="d54d7-126">You can only specify the namespaces and names used to represent the type and its fields or properties in the XML, and the sequence in which the fields and properties appear in the XML:</span></span>

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

  <span data-ttu-id="d54d7-127">Všechno ostatní o struktuře XML, která se používá k reprezentaci typu .NET, je určena <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="d54d7-127">Everything else about the structure of the XML used to represent the .NET type is determined by the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>

- <span data-ttu-id="d54d7-128">Neumožňuje velkou kontrolu nad tím, jak je typ reprezentován v kódu XML, proces serializace je vysoce předvídatelný pro <xref:System.Runtime.Serialization.DataContractSerializer>, a, a, a je tak snazší ho optimalizovat.</span><span class="sxs-lookup"><span data-stu-id="d54d7-128">By not permitting much control over how a type is to be represented in XML, the serialization process becomes highly predictable for the <xref:System.Runtime.Serialization.DataContractSerializer>, and, thereby, easier to optimize.</span></span> <span data-ttu-id="d54d7-129">Praktická výhoda pro návrh <xref:System.Runtime.Serialization.DataContractSerializer> je vyšší výkon, přibližně 10 procent vyšší výkon.</span><span class="sxs-lookup"><span data-stu-id="d54d7-129">A practical benefit of the design of the <xref:System.Runtime.Serialization.DataContractSerializer> is better performance, approximately ten percent better performance.</span></span>

- <span data-ttu-id="d54d7-130">Atributy pro použití s <xref:System.Xml.Serialization.XmlSerializer> parametrem neoznačuje, která pole nebo vlastnosti tohoto typu jsou serializovány do XML, <xref:System.Runtime.Serialization.DataMemberAttribute> zatímco pro použití s parametrem <xref:System.Runtime.Serialization.DataContractSerializer> je explicitně zobrazen, která pole nebo vlastnosti jsou serializovány.</span><span class="sxs-lookup"><span data-stu-id="d54d7-130">The attributes for use with the <xref:System.Xml.Serialization.XmlSerializer> do not indicate which fields or properties of the type are serialized into XML, whereas the <xref:System.Runtime.Serialization.DataMemberAttribute> for use with the <xref:System.Runtime.Serialization.DataContractSerializer> shows explicitly which fields or properties are serialized.</span></span> <span data-ttu-id="d54d7-131">Proto jsou kontrakty dat explicitní smlouvou o struktuře dat, která aplikace odesílá a přijímá.</span><span class="sxs-lookup"><span data-stu-id="d54d7-131">Therefore, data contracts are explicit contracts about the structure of the data that an application is to send and receive.</span></span>

- <span data-ttu-id="d54d7-132">Může přeložit pouze veřejné členy objektu .NET do kódu XML <xref:System.Runtime.Serialization.DataContractSerializer> , lze převést členy objektů do formátu XML bez ohledu na modifikátory přístupu těchto členů. <xref:System.Xml.Serialization.XmlSerializer></span><span class="sxs-lookup"><span data-stu-id="d54d7-132">The <xref:System.Xml.Serialization.XmlSerializer> can only translate the public members of a .NET object into XML, the <xref:System.Runtime.Serialization.DataContractSerializer> can translate the members of objects into XML regardless of the access modifiers of those members.</span></span>

- <span data-ttu-id="d54d7-133">V důsledku toho, že je možné serializovat neveřejné členy typů do XML, <xref:System.Runtime.Serialization.DataContractSerializer> má méně omezení na nejrůznější typy .NET, které může serializovat do XML.</span><span class="sxs-lookup"><span data-stu-id="d54d7-133">As a consequence of being able to serialize the non-public members of types into XML, the <xref:System.Runtime.Serialization.DataContractSerializer> has fewer restrictions on the variety of .NET types that it can serialize into XML.</span></span> <span data-ttu-id="d54d7-134">Konkrétně se může překládat na typy XML, jako <xref:System.Collections.Hashtable> by to <xref:System.Collections.IDictionary> implementovalo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d54d7-134">In particular, it can translate into XML types like <xref:System.Collections.Hashtable> that implement the <xref:System.Collections.IDictionary> interface.</span></span> <span data-ttu-id="d54d7-135"><xref:System.Runtime.Serialization.DataContractSerializer> Je mnohem více pravděpodobné, že je možné serializovat instance všech existujících typů rozhraní .NET do XML, aniž by bylo nutné buď upravit definici typu, nebo vytvořit obálku pro něj.</span><span class="sxs-lookup"><span data-stu-id="d54d7-135">The <xref:System.Runtime.Serialization.DataContractSerializer> is much more likely to be able to serialize the instances of any pre-existing .NET type into XML without having to either modify the definition of the type or develop a wrapper for it.</span></span>

- <span data-ttu-id="d54d7-136">Další důsledky <xref:System.Runtime.Serialization.DataContractSerializer> , jak mít přístup k neveřejným členům typu, je to, že vyžaduje úplný vztah důvěryhodnosti, <xref:System.Xml.Serialization.XmlSerializer> zatímco to není.</span><span class="sxs-lookup"><span data-stu-id="d54d7-136">Another consequence of the <xref:System.Runtime.Serialization.DataContractSerializer> being able to access the non-public members of a type is that it requires full trust, whereas the <xref:System.Xml.Serialization.XmlSerializer> does not.</span></span> <span data-ttu-id="d54d7-137">Oprávnění pro přístup k kódu s úplným vztahem důvěryhodnosti poskytuje úplný přístup ke všem prostředkům v počítači, ke kterým lze přistupovat pomocí přihlašovacích údajů, na jejichž základě se kód spouští.</span><span class="sxs-lookup"><span data-stu-id="d54d7-137">The Full Trust code access permission gives complete access to all resources on a machine that can be accessed using the credentials under which the code is executing.</span></span> <span data-ttu-id="d54d7-138">Tato možnost by se měla používat společně s plně důvěryhodným kódem k přístupu ke všem prostředkům na vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="d54d7-138">This option should be used with care as fully trusted code accesses all resources on your machine.</span></span>

- <span data-ttu-id="d54d7-139"><xref:System.Runtime.Serialization.DataContractSerializer> Zahrnuje určitou podporu pro správu verzí:</span><span class="sxs-lookup"><span data-stu-id="d54d7-139">The <xref:System.Runtime.Serialization.DataContractSerializer> incorporates some support for versioning:</span></span>

  - <span data-ttu-id="d54d7-140"><xref:System.Runtime.Serialization.DataMemberAttribute> Mávlastnost,kterásedápřiřadithodnotěfalsepročleny,kteříjsoupřidanídonovýchverzíkontraktudat,kterénebylypřítomnyvdřívějšíchverzích,atímumožnitaplikacíms<xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> novější verzí smlouvy. dokáže zpracovat starší verze.</span><span class="sxs-lookup"><span data-stu-id="d54d7-140">The <xref:System.Runtime.Serialization.DataMemberAttribute> has an <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> property that can be assigned a value of false for members that are added to new versions of a data contract that were not present in earlier versions, thereby allowing applications with the newer version of the contract to be able to process earlier versions.</span></span>

  - <span data-ttu-id="d54d7-141">Díky tomu, že kontrakt data implementuje <xref:System.Runtime.Serialization.IExtensibleDataObject> rozhraní, může jeden <xref:System.Runtime.Serialization.DataContractSerializer> dovolit předat členům definovaným v novějších verzích kontraktu dat prostřednictvím aplikací s dřívějšími verzemi smlouvy.</span><span class="sxs-lookup"><span data-stu-id="d54d7-141">By having a data contract implement the <xref:System.Runtime.Serialization.IExtensibleDataObject> interface, one can allow the <xref:System.Runtime.Serialization.DataContractSerializer> to pass members defined in newer versions of a data contract through applications with earlier versions of the contract.</span></span>

<span data-ttu-id="d54d7-142">Navzdory všem rozdílům je soubor XML, na který jsou <xref:System.Xml.Serialization.XmlSerializer> serializace typu, ve výchozím nastavení sémanticky totožný s kódem XML, do <xref:System.Runtime.Serialization.DataContractSerializer> kterého serializace typ, za předpokladu, že obor názvů XML je explicitně definován.</span><span class="sxs-lookup"><span data-stu-id="d54d7-142">Despite all of the differences, the XML into which the <xref:System.Xml.Serialization.XmlSerializer> serializes a type by default is semantically identical to the XML into which the <xref:System.Runtime.Serialization.DataContractSerializer> serializes a type, provided the namespace for the XML is explicitly defined.</span></span> <span data-ttu-id="d54d7-143">Následující třída, která má atributy pro použití s oběma serializátory, je přeložena do sémanticky identického XML pomocí <xref:System.Xml.Serialization.XmlSerializer> a: <xref:System.Runtime.Serialization.DataContractAttribute></span><span class="sxs-lookup"><span data-stu-id="d54d7-143">The following class, which has attributes for use with both of the serializers, is translated into semantically identical XML by the <xref:System.Xml.Serialization.XmlSerializer> and by the <xref:System.Runtime.Serialization.DataContractAttribute>:</span></span>

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

<span data-ttu-id="d54d7-144">Sada Windows Software Development Kit (SDK) obsahuje nástroj příkazového řádku, který se nazývá nástroj pro tvorbu [metadat ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="d54d7-144">The Windows software development kit (SDK) includes a command-line tool called the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="d54d7-145">Podobně jako nástroj XSD. exe, který se používá pro webové služby ASP.NET, může Svcutil. exe generovat definice datových typů .NET ze schématu XML.</span><span class="sxs-lookup"><span data-stu-id="d54d7-145">Like the xsd.exe tool used with ASP.NET Web services, Svcutil.exe can generate definitions of .NET data types from XML Schema.</span></span> <span data-ttu-id="d54d7-146">Typy jsou kontrakty dat, pokud <xref:System.Runtime.Serialization.DataContractSerializer> může generovat XML ve formátu definovaném schématem XML; v opačném případě jsou určeny pro serializaci <xref:System.Xml.Serialization.XmlSerializer>pomocí.</span><span class="sxs-lookup"><span data-stu-id="d54d7-146">The types are data contracts if the <xref:System.Runtime.Serialization.DataContractSerializer> can emit XML in the format defined by the XML Schema; otherwise, they are intended for serialization using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="d54d7-147">Svcutil. exe může také vygenerovat schéma XML z kontraktů dat pomocí jeho `dataContractOnly` přepínače.</span><span class="sxs-lookup"><span data-stu-id="d54d7-147">Svcutil.exe can also generate an XML schema from data contracts by using its `dataContractOnly` switch.</span></span>

> [!NOTE]
> <span data-ttu-id="d54d7-148">I když webové služby ASP.NET používají <xref:System.Xml.Serialization.XmlSerializer>, a režim kompatibility ASP.NET WCF způsobuje, že služby WCF napodobují chování webových služeb ASP.NET, možnost kompatibility ASP.NET neomezuje jednu na <xref:System.Xml.Serialization.XmlSerializer>použití.</span><span class="sxs-lookup"><span data-stu-id="d54d7-148">Although ASP.NET Web services use the <xref:System.Xml.Serialization.XmlSerializer>, and WCF ASP.NET compatibility mode makes WCF services mimic the behavior of ASP.NET Web services, the ASP.NET compatibility option does not restrict one to using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="d54d7-149">Ten může stále používat <xref:System.Runtime.Serialization.DataContractSerializer> se službami běžícími v režimu kompatibility ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="d54d7-149">One can still use the <xref:System.Runtime.Serialization.DataContractSerializer> with services running in the ASP.NET compatibility mode.</span></span>

## <a name="service-development"></a><span data-ttu-id="d54d7-150">Vývoj služeb</span><span class="sxs-lookup"><span data-stu-id="d54d7-150">Service Development</span></span>

<span data-ttu-id="d54d7-151">Chcete-li vyvinout službu pomocí ASP.NET, je vlastní pro přidání <xref:System.Web.Services.WebService> atributu do třídy <xref:System.Web.Services.WebMethodAttribute> a do libovolné metody třídy, které mají být operace služby:</span><span class="sxs-lookup"><span data-stu-id="d54d7-151">To develop a service using ASP.NET, it has been customary to add the <xref:System.Web.Services.WebService> attribute to a class, and the <xref:System.Web.Services.WebMethodAttribute> to any of that class’ methods that are to be operations of the service:</span></span>

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

<span data-ttu-id="d54d7-152">ASP.NET 2,0 představil možnost přidání atributu <xref:System.Web.Services.WebService> a <xref:System.Web.Services.WebMethodAttribute> rozhraní, nikoli třídy, a zápis třídy pro implementaci rozhraní:</span><span class="sxs-lookup"><span data-stu-id="d54d7-152">ASP.NET 2.0 introduced the option of adding the attribute <xref:System.Web.Services.WebService> and <xref:System.Web.Services.WebMethodAttribute> to an interface rather than to a class, and writing a class to implement the interface:</span></span>

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

<span data-ttu-id="d54d7-153">Použití této možnosti je upřednostňováno, protože rozhraní s <xref:System.Web.Services.WebService> atributem představuje kontrakt pro operace prováděné službou, které lze znovu použít s různými třídami, které mohou implementovat stejný kontrakt různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="d54d7-153">Using this option is to be preferred, because the interface with the <xref:System.Web.Services.WebService> attribute constitutes a contract for the operations performed by the service that can be reused with various classes that might implement that same contract in different ways.</span></span>

<span data-ttu-id="d54d7-154">Služba WCF je poskytována definováním jednoho nebo více koncových bodů WCF.</span><span class="sxs-lookup"><span data-stu-id="d54d7-154">A WCF service is provided by defining one or more WCF endpoints.</span></span> <span data-ttu-id="d54d7-155">Koncový bod je definovaný adresou, vazbou a kontraktem služby.</span><span class="sxs-lookup"><span data-stu-id="d54d7-155">An endpoint is defined by an address, a binding and a service contract.</span></span> <span data-ttu-id="d54d7-156">Adresa určuje, kde se služba nachází.</span><span class="sxs-lookup"><span data-stu-id="d54d7-156">The address defines where the service is located.</span></span> <span data-ttu-id="d54d7-157">Vazba určuje, jak komunikovat se službou.</span><span class="sxs-lookup"><span data-stu-id="d54d7-157">The binding specifies how to communicate with the service.</span></span> <span data-ttu-id="d54d7-158">Kontrakt služby definuje operace, které může služba provádět.</span><span class="sxs-lookup"><span data-stu-id="d54d7-158">The service contract defines the operations that the service can perform.</span></span>

<span data-ttu-id="d54d7-159">Kontrakt služby je obvykle definován jako první, <xref:System.ServiceModel.ServiceContractAttribute> a to přidáním a <xref:System.ServiceModel.OperationContractAttribute> k rozhraní:</span><span class="sxs-lookup"><span data-stu-id="d54d7-159">The service contract is usually defined first, by adding <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> to an interface:</span></span>

```csharp
[ServiceContract]
public interface IEcho
{
     [OperationContract]
     string Echo(string input);
}
```

<span data-ttu-id="d54d7-160">Určuje, že rozhraní definuje kontrakt služby WCF, <xref:System.ServiceModel.OperationContractAttribute> a označuje, které metody rozhraní definují operace kontraktu služby. <xref:System.ServiceModel.ServiceContractAttribute></span><span class="sxs-lookup"><span data-stu-id="d54d7-160">The <xref:System.ServiceModel.ServiceContractAttribute> specifies that the interface defines a WCF service contract, and the <xref:System.ServiceModel.OperationContractAttribute> indicates which, if any, of the methods of the interface define operations of the service contract.</span></span>

<span data-ttu-id="d54d7-161">Po definování kontraktu služby je implementován ve třídě, tím, že třída implementuje rozhraní, pomocí kterého je definována kontrakt služby:</span><span class="sxs-lookup"><span data-stu-id="d54d7-161">Once a service contract has been defined, it is implemented in a class, by having the class implement the interface by which the service contract is defined:</span></span>

```csharp
public class Service : IEcho
{
    public string Echo(string input)
    {
       return input;
    }
}
```

<span data-ttu-id="d54d7-162">Třída, která implementuje kontrakt služby, se na WCF označuje jako typ služby.</span><span class="sxs-lookup"><span data-stu-id="d54d7-162">A class that implements a service contract is referred to as a service type in WCF.</span></span>

<span data-ttu-id="d54d7-163">Dalším krokem je přidružení adresy a vazby k typu služby.</span><span class="sxs-lookup"><span data-stu-id="d54d7-163">The next step is to associate an address and a binding with a service type.</span></span> <span data-ttu-id="d54d7-164">To se obvykle provádí v konfiguračním souboru, a to buď úpravou souboru přímo, nebo pomocí editoru konfigurace, který je součástí služby WCF.</span><span class="sxs-lookup"><span data-stu-id="d54d7-164">That is typically done in a configuration file, either by editing the file directly, or by using a configuration editor provided with WCF.</span></span> <span data-ttu-id="d54d7-165">Tady je příklad konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="d54d7-165">Here is an example of a configuration file.</span></span>

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

<span data-ttu-id="d54d7-166">Vazba určuje sadu protokolů pro komunikaci s aplikací.</span><span class="sxs-lookup"><span data-stu-id="d54d7-166">The binding specifies the set of protocols for communicating with the application.</span></span> <span data-ttu-id="d54d7-167">V následující tabulce jsou uvedené systémové vazby, které reprezentují běžné možnosti.</span><span class="sxs-lookup"><span data-stu-id="d54d7-167">The following table lists the system-provided bindings that represent common options.</span></span>

|<span data-ttu-id="d54d7-168">Name</span><span class="sxs-lookup"><span data-stu-id="d54d7-168">Name</span></span>|<span data-ttu-id="d54d7-169">Účel</span><span class="sxs-lookup"><span data-stu-id="d54d7-169">Purpose</span></span>|
|----------|-------------|
|<span data-ttu-id="d54d7-170">BasicHttpBinding</span><span class="sxs-lookup"><span data-stu-id="d54d7-170">BasicHttpBinding</span></span>|<span data-ttu-id="d54d7-171">Interoperabilita s webovými službami a klienty, které podporují profil zabezpečení WS-BasicProfile 1,1 a Basic 1,0.</span><span class="sxs-lookup"><span data-stu-id="d54d7-171">Interoperability with Web services and clients supporting the WS-BasicProfile 1.1 and Basic Security Profile 1.0.</span></span>|
|<span data-ttu-id="d54d7-172">WSHttpBinding</span><span class="sxs-lookup"><span data-stu-id="d54d7-172">WSHttpBinding</span></span>|<span data-ttu-id="d54d7-173">Interoperabilita s webovými službami a klienty, které podporují protokoly WS-\* přes protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="d54d7-173">Interoperability with Web services and clients that support the WS-\* protocols over HTTP.</span></span>|
|<span data-ttu-id="d54d7-174">WSDualHttpBinding</span><span class="sxs-lookup"><span data-stu-id="d54d7-174">WSDualHttpBinding</span></span>|<span data-ttu-id="d54d7-175">Duplexní komunikace HTTP, kterou příjemce úvodní zprávy přímo neodpoví počátečnímu odesílateli, ale může přenést libovolný počet odpovědí v časovém intervalu pomocí protokolu HTTP v souladu s protokoly WS-\*.</span><span class="sxs-lookup"><span data-stu-id="d54d7-175">Duplex HTTP communication, by which the receiver of an initial message does not reply directly to the initial sender, but may transmit any number of responses over a period of time by using HTTP in conformity with WS-\* protocols.</span></span>|
|<span data-ttu-id="d54d7-176">WSFederationBinding</span><span class="sxs-lookup"><span data-stu-id="d54d7-176">WSFederationBinding</span></span>|<span data-ttu-id="d54d7-177">Komunikace HTTP, při které se dá přístup k prostředkům služby řídit na základě přihlašovacích údajů vydaných výslovně identifikovaným poskytovatelem přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="d54d7-177">HTTP communication, in which access to the resources of a service can be controlled based on credentials issued by an explicitly-identified credential provider.</span></span>|
|<span data-ttu-id="d54d7-178">NetTcpBinding</span><span class="sxs-lookup"><span data-stu-id="d54d7-178">NetTcpBinding</span></span>|<span data-ttu-id="d54d7-179">Zabezpečená, spolehlivá a vysoce výkonná komunikace mezi softwarovými entitami WCF v síti.</span><span class="sxs-lookup"><span data-stu-id="d54d7-179">Secure, reliable, high-performance communication between WCF software entities across a network.</span></span>|
|<span data-ttu-id="d54d7-180">NetNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="d54d7-180">NetNamedPipeBinding</span></span>|<span data-ttu-id="d54d7-181">Zabezpečená, spolehlivá a vysoce výkonná komunikace mezi entitami softwaru WCF ve stejném počítači.</span><span class="sxs-lookup"><span data-stu-id="d54d7-181">Secure, reliable, high-performance communication between WCF software entities on the same machine.</span></span>|
|<span data-ttu-id="d54d7-182">NetMsmqBinding</span><span class="sxs-lookup"><span data-stu-id="d54d7-182">NetMsmqBinding</span></span>|<span data-ttu-id="d54d7-183">Komunikace mezi softwarovými entitami WCF pomocí služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="d54d7-183">Communication between WCF software entities by using MSMQ.</span></span>|
|<span data-ttu-id="d54d7-184">MsmqIntegrationBinding</span><span class="sxs-lookup"><span data-stu-id="d54d7-184">MsmqIntegrationBinding</span></span>|<span data-ttu-id="d54d7-185">Komunikace mezi entitou softwaru WCF a jinou softwarovou entitou pomocí služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="d54d7-185">Communication between a WCF software entity and another software entity by using MSMQ.</span></span>|
|<span data-ttu-id="d54d7-186">NetPeerTcpBinding</span><span class="sxs-lookup"><span data-stu-id="d54d7-186">NetPeerTcpBinding</span></span>|<span data-ttu-id="d54d7-187">Komunikace mezi softwarovými entitami WCF pomocí sítě Windows peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="d54d7-187">Communication between WCF software entities by using Windows Peer-to-Peer Networking.</span></span>|

<span data-ttu-id="d54d7-188">Vazba <xref:System.ServiceModel.BasicHttpBinding>poskytovaná systémem zahrnuje sadu protokolů podporovaných ASP.NET webovými službami.</span><span class="sxs-lookup"><span data-stu-id="d54d7-188">The system-provided binding, <xref:System.ServiceModel.BasicHttpBinding>, incorporates the set of protocols supported by ASP.NET Web services.</span></span>

<span data-ttu-id="d54d7-189">Vlastní vazby pro aplikace WCF jsou snadno definovány jako kolekce tříd prvků vazby, které WCF používá k implementaci jednotlivých protokolů.</span><span class="sxs-lookup"><span data-stu-id="d54d7-189">Custom bindings for WCF applications are easily defined as collections of the binding element classes that WCF uses to implement individual protocols.</span></span> <span data-ttu-id="d54d7-190">Můžete napsat nové prvky vazby, které budou představovat další protokoly.</span><span class="sxs-lookup"><span data-stu-id="d54d7-190">New binding elements can be written to represent additional protocols.</span></span>

<span data-ttu-id="d54d7-191">Vnitřní chování typů služeb lze upravit pomocí vlastností rodiny tříd nazvaných chování.</span><span class="sxs-lookup"><span data-stu-id="d54d7-191">The internal behavior of service types can be adjusted using the properties of a family of classes called behaviors.</span></span> <span data-ttu-id="d54d7-192">Zde je třída použita k určení, zda má být typ služby vícevláknový. <xref:System.ServiceModel.ServiceBehaviorAttribute></span><span class="sxs-lookup"><span data-stu-id="d54d7-192">Here, the <xref:System.ServiceModel.ServiceBehaviorAttribute> class is used to specify that the service type is to be multithreaded.</span></span>

```csharp
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple]
public class DerivativesCalculatorServiceType: IDerivativesCalculator
```

<span data-ttu-id="d54d7-193">Některá chování, <xref:System.ServiceModel.ServiceBehaviorAttribute>například, jsou atributy.</span><span class="sxs-lookup"><span data-stu-id="d54d7-193">Some behaviors, like <xref:System.ServiceModel.ServiceBehaviorAttribute>, are attributes.</span></span> <span data-ttu-id="d54d7-194">Ostatní, ty, které by správci chtěli nastavit, je možné upravit v konfiguraci aplikace.</span><span class="sxs-lookup"><span data-stu-id="d54d7-194">Others, the ones with properties that administrators would want to set, can be modified in the configuration of an application.</span></span>

<span data-ttu-id="d54d7-195">V typech programovacích služeb je časté použití <xref:System.ServiceModel.OperationContext> třídy vytvořeno.</span><span class="sxs-lookup"><span data-stu-id="d54d7-195">In programming service types, frequent use is made of the <xref:System.ServiceModel.OperationContext> class.</span></span> <span data-ttu-id="d54d7-196">Jeho statická <xref:System.ServiceModel.OperationContext.Current%2A> vlastnost poskytuje přístup k informacím o kontextu, ve kterém je operace spuštěná.</span><span class="sxs-lookup"><span data-stu-id="d54d7-196">Its static <xref:System.ServiceModel.OperationContext.Current%2A> property provides access to information about the context in which an operation is running.</span></span> <span data-ttu-id="d54d7-197"><xref:System.ServiceModel.OperationContext>je podobná <xref:System.Web.HttpContext> třídám a <xref:System.EnterpriseServices.ContextUtil> .</span><span class="sxs-lookup"><span data-stu-id="d54d7-197"><xref:System.ServiceModel.OperationContext> is similar to both the <xref:System.Web.HttpContext> and <xref:System.EnterpriseServices.ContextUtil> classes.</span></span>

## <a name="hosting"></a><span data-ttu-id="d54d7-198">Hostování</span><span class="sxs-lookup"><span data-stu-id="d54d7-198">Hosting</span></span>

<span data-ttu-id="d54d7-199">Webové služby ASP.NET jsou kompilovány do sestavení knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="d54d7-199">ASP.NET Web services are compiled into a class library assembly.</span></span> <span data-ttu-id="d54d7-200">K dispozici je soubor s názvem soubor služby s příponou. asmx a obsahuje `@ WebService` direktivu, která identifikuje třídu, která obsahuje kód pro službu a sestavení, ve kterém se nachází.</span><span class="sxs-lookup"><span data-stu-id="d54d7-200">A file called the service file is provided that has the extension .asmx and contains an `@ WebService` directive that identifies the class that contains the code for the service and the assembly in which it is located.</span></span>

`<%@ WebService Language="C#" Class="Service,ServiceAssembly" %>`

<span data-ttu-id="d54d7-201">Soubor služby je zkopírován do kořenového adresáře aplikace ASP.NET v Internetová informační služba (IIS) a sestavení je zkopírováno do podadresáře \Bin kořenového adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="d54d7-201">The service file is copied into an ASP.NET application root in Internet Information Services (IIS), and the assembly is copied into the \bin subdirectory of that application root.</span></span> <span data-ttu-id="d54d7-202">Aplikace je pak přístupná pomocí adresy URL (Uniform Resource Locator) souboru služby v kořenovém adresáři aplikace.</span><span class="sxs-lookup"><span data-stu-id="d54d7-202">The application is then accessible by using the uniform resource locator (URL) of the service file in the application root.</span></span>

<span data-ttu-id="d54d7-203">Služby WCF je možné snadno hostovat v rámci služby IIS 5,1 nebo 6,0, což je služba WAS (Windows Process Activation Service), která se poskytuje jako součást služby IIS 7,0, a v rámci libovolné aplikace .NET.</span><span class="sxs-lookup"><span data-stu-id="d54d7-203">WCF services can readily be hosted within IIS 5.1 or 6.0, the Windows Process Activation Service (WAS) that is provided as part of IIS 7.0, and within any .NET application.</span></span> <span data-ttu-id="d54d7-204">Aby mohla služba hostovat službu ve službě IIS 5,1 nebo 6,0, musí jako komunikační transportní protokol používat protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="d54d7-204">To host a service in IIS 5.1 or 6.0, the service must use HTTP as the communications transport protocol.</span></span>

<span data-ttu-id="d54d7-205">Chcete-li hostovat službu ve službě IIS 5,1, 6,0 nebo v nástroji, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="d54d7-205">To host a service within IIS 5.1, 6.0 or within WAS, use the follows steps:</span></span>

1. <span data-ttu-id="d54d7-206">Zkompilujte typ služby do sestavení knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="d54d7-206">Compile the service type into a class library assembly.</span></span>

2. <span data-ttu-id="d54d7-207">Vytvořte soubor služby s příponou. svc s `@ ServiceHost` direktivou pro identifikaci typu služby:</span><span class="sxs-lookup"><span data-stu-id="d54d7-207">Create a service file with a .svc extension with an `@ ServiceHost` directive to identify the service type:</span></span>

    `<%@ServiceHost language="c#" Service="MyService" %>`

3. <span data-ttu-id="d54d7-208">Zkopírujte soubor služby do virtuálního adresáře a sestavení do podadresáře \Bin tohoto virtuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="d54d7-208">Copy the service file into a virtual directory, and the assembly into the \bin subdirectory of that virtual directory.</span></span>

4. <span data-ttu-id="d54d7-209">Zkopírujte konfigurační soubor do virtuálního adresáře a pojmenujte ho Web. config.</span><span class="sxs-lookup"><span data-stu-id="d54d7-209">Copy the configuration file into the virtual directory, and name it Web.config.</span></span>

<span data-ttu-id="d54d7-210">Aplikace je pak přístupná pomocí adresy URL souboru služby v kořenovém adresáři aplikace.</span><span class="sxs-lookup"><span data-stu-id="d54d7-210">The application is then accessible by using the URL of the service file in the application root.</span></span>

<span data-ttu-id="d54d7-211">Chcete-li hostovat službu WCF v rámci aplikace .NET, zkompilujte typ služby do sestavení knihovny tříd, na které odkazuje aplikace, a Programujte aplikaci pro hostování služby pomocí <xref:System.ServiceModel.ServiceHost> třídy.</span><span class="sxs-lookup"><span data-stu-id="d54d7-211">To host a WCF service within a .NET application, compile the service type into a class library assembly referenced by the application, and program the application to host the service using the <xref:System.ServiceModel.ServiceHost> class.</span></span> <span data-ttu-id="d54d7-212">Následuje příklad základního vyžadovaného programování:</span><span class="sxs-lookup"><span data-stu-id="d54d7-212">The following is an example of the basic programming required:</span></span>

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

<span data-ttu-id="d54d7-213">Tento příklad ukazuje, jak jsou zadány adresy jednoho nebo více přenosových protokolů v konstrukci <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="d54d7-213">This example shows how addresses for one or more transport protocols are specified in the construction of a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="d54d7-214">Tyto adresy se označují jako základní adresy.</span><span class="sxs-lookup"><span data-stu-id="d54d7-214">These addresses are referred to as base addresses.</span></span>

<span data-ttu-id="d54d7-215">Adresa zadaná pro libovolný koncový bod služby WCF je adresa relativní k základní adrese hostitele koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="d54d7-215">The address provided for any endpoint of a WCF service is an address relative to a base address of the endpoint’s host.</span></span> <span data-ttu-id="d54d7-216">Hostitel může mít jednu základní adresu pro každý komunikační transportní protokol.</span><span class="sxs-lookup"><span data-stu-id="d54d7-216">The host can have one base address for each communication transport protocol.</span></span> <span data-ttu-id="d54d7-217">V ukázkové konfiguraci v předchozím konfiguračním souboru <xref:System.ServiceModel.BasicHttpBinding> používá vybraný koncový bod HTTP jako transportní protokol, takže adresa `EchoService`koncového bodu je relativní vzhledem k základní adrese http hostitele.</span><span class="sxs-lookup"><span data-stu-id="d54d7-217">In the sample configuration in the preceding configuration file, the <xref:System.ServiceModel.BasicHttpBinding> selected for the endpoint uses HTTP as the transport protocol, so the address of the endpoint, `EchoService`, is relative to the host’s HTTP base address.</span></span> <span data-ttu-id="d54d7-218">V případě hostitele v předchozím příkladu je `http://www.contoso.com:8000/`základní adresa http.</span><span class="sxs-lookup"><span data-stu-id="d54d7-218">In the case of the host in the preceding example, the HTTP base address is `http://www.contoso.com:8000/`.</span></span> <span data-ttu-id="d54d7-219">V případě služby hostované v rámci služby IIS nebo WAS je základní adresou adresa URL souboru služby služby.</span><span class="sxs-lookup"><span data-stu-id="d54d7-219">For a service hosted within IIS or WAS, the base address is the URL of the service’s service file.</span></span>

<span data-ttu-id="d54d7-220">Pro použití možnosti režimu kompatibility WCF ASP.NET je možné použít jenom služby hostované ve službě IIS nebo WAS a které jsou nakonfigurované s HTTP jako transportní protokol.</span><span class="sxs-lookup"><span data-stu-id="d54d7-220">Only services hosted in IIS or WAS, and which are configured with HTTP as the transport protocol exclusively, can be made to use WCF ASP.NET compatibility mode option.</span></span> <span data-ttu-id="d54d7-221">Zapnutí této možnosti vyžaduje následující kroky.</span><span class="sxs-lookup"><span data-stu-id="d54d7-221">Turning that option on requires the following steps.</span></span>

1. <span data-ttu-id="d54d7-222">Programátor musí přidat <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> atribut do typu služby a určit, že režim kompatibility ASP.NET je buď povolený, nebo povinný.</span><span class="sxs-lookup"><span data-stu-id="d54d7-222">The programmer must add the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> attribute to the service type and specify that ASP.NET compatibility mode is either allowed or required.</span></span>

    ```csharp
    [System.ServiceModel.Activation.AspNetCompatibilityRequirements(
          RequirementsMode=AspNetCompatibilityRequirementsMode.Require)]
    public class DerivativesCalculatorServiceType: IDerivativesCalculator
    ```

2. <span data-ttu-id="d54d7-223">Správce musí aplikaci nakonfigurovat tak, aby používala režim kompatibility ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="d54d7-223">The administrator must configure the application to use the ASP.NET compatibility mode.</span></span>

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

    <span data-ttu-id="d54d7-224">Aplikace WCF je také možné nakonfigurovat tak, aby používaly. asmx jako přípona svých souborů služby, nikoli. svc.</span><span class="sxs-lookup"><span data-stu-id="d54d7-224">WCF applications can also be configured to use .asmx as the extension for their service files rather than .svc.</span></span>

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

    <span data-ttu-id="d54d7-225">Tato možnost vám může ušetřit při úpravách klientů, kteří jsou nakonfigurováni na používání adres URL souborů služby. asmx při úpravě služby na použití WCF.</span><span class="sxs-lookup"><span data-stu-id="d54d7-225">That option can save you from having to modify clients that are configured to use the URLs of .asmx service files when modifying a service to use WCF.</span></span>

## <a name="client-development"></a><span data-ttu-id="d54d7-226">Vývoj klienta</span><span class="sxs-lookup"><span data-stu-id="d54d7-226">Client Development</span></span>

<span data-ttu-id="d54d7-227">Klienti pro webové služby ASP.NET se generují pomocí nástroje příkazového řádku WSDL. exe, který jako vstup poskytuje adresu URL souboru. asmx.</span><span class="sxs-lookup"><span data-stu-id="d54d7-227">Clients for ASP.NET Web services are generated using the command-line tool, WSDL.exe, which provides the URL of the .asmx file as input.</span></span> <span data-ttu-id="d54d7-228">Odpovídající nástroj poskytovaný službou WCF je [Nástroj pro nástroj pro metadata ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="d54d7-228">The corresponding tool provided by WCF is [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="d54d7-229">Generuje modul kódu s definicí kontraktu služby a definicí třídy klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="d54d7-229">It generates a code module with the definition of the service contract and the definition of a WCF client class.</span></span> <span data-ttu-id="d54d7-230">Také generuje konfigurační soubor s adresou a vazbou služby.</span><span class="sxs-lookup"><span data-stu-id="d54d7-230">It also generates a configuration file with the address and binding of the service.</span></span>

<span data-ttu-id="d54d7-231">Při programování klienta vzdálené služby je obecně vhodné programovat podle asynchronního vzoru.</span><span class="sxs-lookup"><span data-stu-id="d54d7-231">In programming a client of a remote service it is generally advisable to program according to an asynchronous pattern.</span></span> <span data-ttu-id="d54d7-232">Kód vygenerovaný nástrojem WSDL. exe vždy poskytuje synchronní i asynchronní vzor ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="d54d7-232">The code generated by the WSDL.exe tool always provides for both a synchronous and an asynchronous pattern by default.</span></span> <span data-ttu-id="d54d7-233">Kód vygenerovaný nástrojem pro dodávání [metadat ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) může poskytovat buď vzorek.</span><span class="sxs-lookup"><span data-stu-id="d54d7-233">The code generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) can provide for either pattern.</span></span> <span data-ttu-id="d54d7-234">Ve výchozím nastavení poskytuje synchronní vzor.</span><span class="sxs-lookup"><span data-stu-id="d54d7-234">It provides for the synchronous pattern by default.</span></span> <span data-ttu-id="d54d7-235">Pokud je nástroj spuštěn s `/async` přepínačem, pak generovaný kód poskytne asynchronní vzorek.</span><span class="sxs-lookup"><span data-stu-id="d54d7-235">If the tool is executed with the `/async` switch, then the generated code provides for the asynchronous pattern.</span></span>

<span data-ttu-id="d54d7-236">Není zaručeno, že názvy v třídách klienta WCF vygenerovaných ASP. Nástroj WSDL. exe nástroje NET standardně odpovídá názvům ve třídách klienta WCF vygenerovaných nástrojem Svcutil. exe.</span><span class="sxs-lookup"><span data-stu-id="d54d7-236">There is no guarantee that names in the WCF client classes generated by ASP.NET’s WSDL.exe tool, by default, match the names in WCF client classes generated by the Svcutil.exe tool.</span></span> <span data-ttu-id="d54d7-237">Konkrétně názvy vlastností tříd, které musí být serializovány pomocí <xref:System.Xml.Serialization.XmlSerializer> , jsou ve výchozím nastavení uděleny vlastnosti přípona v kódu generovaném nástrojem Svcutil. exe, který není v případě nástroje WSDL. exe.</span><span class="sxs-lookup"><span data-stu-id="d54d7-237">In particular, the names of the properties of classes that have to be serialized using the <xref:System.Xml.Serialization.XmlSerializer> are, by default, given the suffix Property in the code generated by the Svcutil.exe tool, which is not the case with the WSDL.exe tool.</span></span>

## <a name="message-representation"></a><span data-ttu-id="d54d7-238">Reprezentace zprávy</span><span class="sxs-lookup"><span data-stu-id="d54d7-238">Message Representation</span></span>

<span data-ttu-id="d54d7-239">Hlavičky zpráv SOAP odesílaných a přijímaných webovými službami ASP.NET se dají přizpůsobit.</span><span class="sxs-lookup"><span data-stu-id="d54d7-239">The headers of the SOAP messages sent and received by ASP.NET Web services can be customized.</span></span> <span data-ttu-id="d54d7-240">Třída je odvozena z <xref:System.Web.Services.Protocols.SoapHeader> pro definování struktury záhlaví a <xref:System.Web.Services.Protocols.SoapHeaderAttribute> pak slouží k označení přítomnosti záhlaví.</span><span class="sxs-lookup"><span data-stu-id="d54d7-240">A class is derived from <xref:System.Web.Services.Protocols.SoapHeader> to define the structure of the header, and then the <xref:System.Web.Services.Protocols.SoapHeaderAttribute> is used to indicate the presence of the header.</span></span>

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

<span data-ttu-id="d54d7-241">Služba WCF poskytuje atributy, <xref:System.ServiceModel.MessageContractAttribute> <xref:System.ServiceModel.MessageHeaderAttribute>, a <xref:System.ServiceModel.MessageBodyMemberAttribute> pro popis struktury zpráv SOAP odesílaných a přijímaných službou.</span><span class="sxs-lookup"><span data-stu-id="d54d7-241">The WCF provides the attributes, <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute>, and <xref:System.ServiceModel.MessageBodyMemberAttribute> to describe the structure of the SOAP messages sent and received by a service.</span></span>

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

<span data-ttu-id="d54d7-242">Tato syntaxe poskytuje explicitní reprezentace struktury zpráv, zatímco struktura zpráv je odvozena kódem webové služby ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="d54d7-242">This syntax yields an explicit representation of the structure of the messages, whereas the structure of messages is implied by the code of an ASP.NET Web service.</span></span> <span data-ttu-id="d54d7-243">Také v syntaxi ASP.NET jsou hlavičky zpráv reprezentovány jako vlastnosti služby, jako je `ProtocolHeader` například vlastnost v předchozím příkladu, zatímco v syntaxi služby WCF jsou přesněji reprezentovány jako vlastnosti zpráv.</span><span class="sxs-lookup"><span data-stu-id="d54d7-243">Also, in the ASP.NET syntax, message headers are represented as properties of the service, such as the `ProtocolHeader` property in the previous example, whereas in WCF syntax, they are more accurately represented as properties of messages.</span></span> <span data-ttu-id="d54d7-244">WCF také umožňuje přidání záhlaví zpráv do konfigurace koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="d54d7-244">Also, WCF allows message headers to be added to the configuration of endpoints.</span></span>

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

<span data-ttu-id="d54d7-245">Tato možnost umožňuje vyhnout se jakémukoli odkazu na záhlaví protokolu infrastruktury v kódu pro klienta nebo službu: záhlaví jsou přidána do zpráv z důvodu konfigurace koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="d54d7-245">That option allows you to avoid any reference to infrastructural protocol headers in the code for a client or service: the headers are added to messages because of how the endpoint is configured.</span></span>

## <a name="service-description"></a><span data-ttu-id="d54d7-246">Popis služby</span><span class="sxs-lookup"><span data-stu-id="d54d7-246">Service Description</span></span>

<span data-ttu-id="d54d7-247">Vydání požadavku HTTP GET pro soubor. asmx webové služby ASP.NET s dotazem WSDL způsobí, že ASP.NET generuje WSDL pro popis služby.</span><span class="sxs-lookup"><span data-stu-id="d54d7-247">Issuing an HTTP GET request for the .asmx file of an ASP.NET Web service with the query WSDL causes ASP.NET to generate WSDL to describe the service.</span></span> <span data-ttu-id="d54d7-248">Vrátí tento prvek WSDL jako odpověď na požadavek.</span><span class="sxs-lookup"><span data-stu-id="d54d7-248">It returns that WSDL as the response to the request.</span></span>

<span data-ttu-id="d54d7-249">ASP.NET 2,0 umožňuje ověřit, jestli je služba kompatibilní se základním profilem 1,1 organizace pro interoperabilitu webových služeb (WS-I) a jestli se má do svého rozhraní WSDL vložit deklarace identity, kterou služba dodržuje.</span><span class="sxs-lookup"><span data-stu-id="d54d7-249">ASP.NET 2.0 made it possible to validate that a service is compliant with the Basic Profile 1.1 of the Web Services-Interoperability Organization (WS-I), and to insert a claim that the service is compliant into its WSDL.</span></span> <span data-ttu-id="d54d7-250">To se provádí pomocí `ConformsTo` parametrů <xref:System.Web.Services.WebServiceBindingAttribute> a `EmitConformanceClaims` atributu.</span><span class="sxs-lookup"><span data-stu-id="d54d7-250">That is done using the `ConformsTo` and `EmitConformanceClaims` parameters of the <xref:System.Web.Services.WebServiceBindingAttribute> attribute.</span></span>

```csharp
[WebService(Namespace = "http://tempuri.org/")]
[WebServiceBinding(
     ConformsTo = WsiProfiles.BasicProfile1_1,
     EmitConformanceClaims=true)]
public interface IEcho
```

<span data-ttu-id="d54d7-251">Rozhraní WSDL, které ASP.NET generuje pro službu, lze přizpůsobit.</span><span class="sxs-lookup"><span data-stu-id="d54d7-251">The WSDL that ASP.NET generates for a service can be customized.</span></span> <span data-ttu-id="d54d7-252">Vlastní nastavení se provádí vytvořením odvozené třídy <xref:System.Web.Services.Description.ServiceDescriptionFormatExtension> pro přidání položek do WSDL.</span><span class="sxs-lookup"><span data-stu-id="d54d7-252">Customizations are made by creating a derived class of <xref:System.Web.Services.Description.ServiceDescriptionFormatExtension> to add items to the WSDL.</span></span>

<span data-ttu-id="d54d7-253">Vydání požadavku HTTP GET s dotazem WSDL pro soubor. svc služby WCF s koncovým bodem HTTP hostovaným ve službě IIS 51, 6,0 nebo způsobilo, že WCF reaguje na jazyk WSDL, aby popisoval službu.</span><span class="sxs-lookup"><span data-stu-id="d54d7-253">Issuing an HTTP GET request with the query WSDL for the .svc file of a WCF service with an HTTP endpoint hosted within IIS 51, 6.0 or WAS causes WCF to respond with WSDL to describe the service.</span></span> <span data-ttu-id="d54d7-254">Vydání požadavku HTTP GET s dotazem WSDL na základní adresu HTTP služby hostované v aplikaci .NET má stejný účinek, pokud je httpGetEnabled nastaveno na hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="d54d7-254">Issuing an HTTP GET request with the query WSDL to the HTTP base address of a service hosted within a .NET application has the same effect if httpGetEnabled is set to true.</span></span>

<span data-ttu-id="d54d7-255">WCF ale také reaguje na požadavky WS-MetadataExchange s WSDL, které generuje pro popis služby.</span><span class="sxs-lookup"><span data-stu-id="d54d7-255">However, WCF also responds to WS-MetadataExchange requests with WSDL that it generates to describe a service.</span></span> <span data-ttu-id="d54d7-256">Webové služby ASP.NET nemají integrovanou podporu pro požadavky WS-MetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="d54d7-256">ASP.NET Web services do not have built-in support for WS-MetadataExchange requests.</span></span>

<span data-ttu-id="d54d7-257">WSDL, kterou WCF generuje, může být výrazně přizpůsobená.</span><span class="sxs-lookup"><span data-stu-id="d54d7-257">The WSDL that WCF generates can be extensively customized.</span></span> <span data-ttu-id="d54d7-258"><xref:System.ServiceModel.Description.ServiceMetadataBehavior> Třída poskytuje určitá zařízení pro přizpůsobení rozhraní WSDL.</span><span class="sxs-lookup"><span data-stu-id="d54d7-258">The <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class provides some facilities for customizing the WSDL.</span></span> <span data-ttu-id="d54d7-259">WCF je také možné nakonfigurovat tak, aby negenerovalo WSDL, ale místo toho používat statický soubor WSDL v dané adrese URL.</span><span class="sxs-lookup"><span data-stu-id="d54d7-259">The WCF can also be configured to not generate WSDL, but rather to use a static WSDL file at a given URL.</span></span>

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

## <a name="exception-handling"></a><span data-ttu-id="d54d7-260">Zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="d54d7-260">Exception Handling</span></span>

<span data-ttu-id="d54d7-261">V ASP.NET webové služby se neošetřené výjimky vrátí klientům jako chyby protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="d54d7-261">In ASP.NET Web services, unhandled exceptions are returned to clients as SOAP faults.</span></span> <span data-ttu-id="d54d7-262">Můžete také explicitně vyvolat instance <xref:System.Web.Services.Protocols.SoapException> třídy a mít větší kontrolu nad obsahem chyby protokolu SOAP, která se přenáší klientovi.</span><span class="sxs-lookup"><span data-stu-id="d54d7-262">You can also explicitly throw instances of the <xref:System.Web.Services.Protocols.SoapException> class and have more control over the content of the SOAP fault that gets transmitted to the client.</span></span>

<span data-ttu-id="d54d7-263">Ve službách WCF nejsou neošetřené výjimky vraceny klientům jako chyby protokolu SOAP, aby se zabránilo neúmyslnému zveřejnění citlivých informací prostřednictvím výjimek.</span><span class="sxs-lookup"><span data-stu-id="d54d7-263">In WCF services, unhandled exceptions are not returned to clients as SOAP faults to prevent sensitive information being inadvertently exposed through the exceptions.</span></span> <span data-ttu-id="d54d7-264">Nastavení konfigurace je k dispozici, aby byly neošetřené výjimky vraceny klientům pro účely ladění.</span><span class="sxs-lookup"><span data-stu-id="d54d7-264">A configuration setting is provided to have unhandled exceptions returned to clients for the purpose of debugging.</span></span>

<span data-ttu-id="d54d7-265">Chcete-li vrátit chyby protokolu SOAP klientům, můžete vyvolat instance obecného typu <xref:System.ServiceModel.FaultException%601>pomocí typu kontraktu dat jako obecného typu.</span><span class="sxs-lookup"><span data-stu-id="d54d7-265">To return SOAP faults to clients, you can throw instances of the generic type, <xref:System.ServiceModel.FaultException%601>, using the data contract type as the generic type.</span></span> <span data-ttu-id="d54d7-266">Můžete také přidat <xref:System.ServiceModel.FaultContractAttribute> atributy do operací a určit tak chyby, které může operace vracet.</span><span class="sxs-lookup"><span data-stu-id="d54d7-266">You can also add <xref:System.ServiceModel.FaultContractAttribute> attributes to operations to specify the faults that an operation might yield.</span></span>

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

<span data-ttu-id="d54d7-267">Výsledkem je, že jsou možné chyby inzerované v rozhraní WSDL pro službu, což umožňuje programátorům v klientských chybách odhadnout, které chyby mohou být výsledkem operace, a zapsat příslušné příkazy Catch.</span><span class="sxs-lookup"><span data-stu-id="d54d7-267">Doing so results in the possible faults being advertised in the WSDL for the service, allowing client programmers to anticipate which faults can result from an operation, and write the appropriate catch statements.</span></span>

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

## <a name="state-management"></a><span data-ttu-id="d54d7-268">Správa stavu</span><span class="sxs-lookup"><span data-stu-id="d54d7-268">State Management</span></span>

<span data-ttu-id="d54d7-269">Třída použitá k implementaci webové služby ASP.NET může být odvozena z <xref:System.Web.Services.WebService>.</span><span class="sxs-lookup"><span data-stu-id="d54d7-269">The class used to implement an ASP.NET Web service may be derived from <xref:System.Web.Services.WebService>.</span></span>

```csharp
public class Service : WebService, IEcho
{

 public string Echo(string input)
 {
  return input;
 }
}
```

<span data-ttu-id="d54d7-270">V takovém případě může být třída naprogramována tak, aby pro <xref:System.Web.Services.WebService> <xref:System.Web.HttpContext> přístup k objektu použila kontextovou vlastnost základní třídy.</span><span class="sxs-lookup"><span data-stu-id="d54d7-270">In that case, the class can be programmed to use the <xref:System.Web.Services.WebService> base class’ Context property to access a <xref:System.Web.HttpContext> object.</span></span> <span data-ttu-id="d54d7-271"><xref:System.Web.HttpContext> Objekt lze použít k aktualizaci a načtení informací o stavu aplikace pomocí jeho vlastnosti aplikace a lze jej použít k aktualizaci a načtení informací o stavu relace pomocí vlastnosti relace.</span><span class="sxs-lookup"><span data-stu-id="d54d7-271">The <xref:System.Web.HttpContext> object can be used to update and retrieve application state information by using its Application property, and can be used to update and retrieve session state information by using its Session property.</span></span>

<span data-ttu-id="d54d7-272">ASP.NET poskytuje značnou kontrolu nad tím, kde jsou informace o stavu relace, ke kterým se <xref:System.Web.HttpContext> přistupovaly pomocí vlastnosti relace ve skutečnosti uložené.</span><span class="sxs-lookup"><span data-stu-id="d54d7-272">ASP.NET provides considerable control over where the session state information accessed by using the Session property of the <xref:System.Web.HttpContext> is actually stored.</span></span> <span data-ttu-id="d54d7-273">Může být uložen v souborech cookie, v databázi, v paměti aktuálního serveru nebo v paměti určeného serveru.</span><span class="sxs-lookup"><span data-stu-id="d54d7-273">It may be stored in cookies, in a database, in the memory of the current server, or in the memory of a designated server.</span></span> <span data-ttu-id="d54d7-274">Tato volba se provádí v konfiguračním souboru služby.</span><span class="sxs-lookup"><span data-stu-id="d54d7-274">The choice is made in the service’s configuration file.</span></span>

<span data-ttu-id="d54d7-275">WCF poskytuje rozšiřitelné objekty pro správu stavů.</span><span class="sxs-lookup"><span data-stu-id="d54d7-275">The WCF provides extensible objects for state management.</span></span> <span data-ttu-id="d54d7-276">Rozšiřitelné objekty jsou objekty, <xref:System.ServiceModel.IExtensibleObject%601>které implementují.</span><span class="sxs-lookup"><span data-stu-id="d54d7-276">Extensible objects are objects that implement <xref:System.ServiceModel.IExtensibleObject%601>.</span></span> <span data-ttu-id="d54d7-277">Nejdůležitější rozšiřitelné objekty jsou <xref:System.ServiceModel.ServiceHostBase> a. <xref:System.ServiceModel.InstanceContext></span><span class="sxs-lookup"><span data-stu-id="d54d7-277">The most important extensible objects are <xref:System.ServiceModel.ServiceHostBase> and <xref:System.ServiceModel.InstanceContext>.</span></span> <span data-ttu-id="d54d7-278">`ServiceHostBase`umožňuje zachovat stav, ke kterému mají přístup všechny instance všech typů služeb na stejném hostiteli, `InstanceContext` a umožňuje zachovat stav, ke kterému může přistupovat jakýkoli kód spuštěný ve stejné instanci typu služby.</span><span class="sxs-lookup"><span data-stu-id="d54d7-278">`ServiceHostBase` allows you to maintain state that all of the instances of all of the service types on the same host can access, while `InstanceContext` allows you to maintain state that can be accessed by any code running within the same instance of a service type.</span></span>

<span data-ttu-id="d54d7-279">Zde je typ `TradingSystem`služby,, <xref:System.ServiceModel.ServiceBehaviorAttribute> má, který určuje, že všechna volání ze stejné instance klienta služby WCF jsou směrována do stejné instance typu služby.</span><span class="sxs-lookup"><span data-stu-id="d54d7-279">Here, the service type, `TradingSystem`, has a <xref:System.ServiceModel.ServiceBehaviorAttribute> that specifies that all calls from the same WCF client instance are routed to the same instance of the service type.</span></span>

```csharp
[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerSession)]
public class TradingSystem: ITradingService
```

<span data-ttu-id="d54d7-280">Třída `DealData`definuje stav, ke kterému lze přistupovat jakýkoli kód spuštěný ve stejné instanci typu služby.</span><span class="sxs-lookup"><span data-stu-id="d54d7-280">The class, `DealData`, defines state that can be accessed by any code running in the same instance of a service type.</span></span>

```csharp
internal class DealData: IExtension<InstanceContext>
{
 public string DealIdentifier = null;
 public Trade[] Trades = null;
}
```

<span data-ttu-id="d54d7-281">V kódu typu služby, který implementuje jednu z operací kontraktu služby, `DealData` je objekt stavu přidán do stavu aktuální instance typu služby.</span><span class="sxs-lookup"><span data-stu-id="d54d7-281">In the code of the service type that implements one of the operations of the service contract, a `DealData` state object is added to the state of the current instance of the service type.</span></span>

```csharp
string ITradingService.BeginDeal()
{
 string dealIdentifier = Guid.NewGuid().ToString();
 DealData state = new DealData(dealIdentifier);
 OperationContext.Current.InstanceContext.Extensions.Add(state);
 return dealIdentifier;
}
```

<span data-ttu-id="d54d7-282">Tento stavový objekt lze poté načíst a upravit pomocí kódu, který implementuje jinou operaci kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="d54d7-282">That state object can then be retrieved and modified by the code that implements another of the service contract’s operations.</span></span>

```csharp
void ITradingService.AddTrade(Trade trade)
{
 DealData dealData =  OperationContext.Current.InstanceContext.Extensions.Find<DealData>();
 dealData.AddTrade(trade);
}
```

<span data-ttu-id="d54d7-283">Zatímco ASP.NET poskytuje kontrolu nad tím <xref:System.Web.HttpContext> , kde jsou ve skutečnosti uložené informace o stavu ve třídě, WCF, alespoň v její počáteční verzi, neposkytuje žádnou kontrolu nad tím, kde jsou uložené rozšiřitelné objekty.</span><span class="sxs-lookup"><span data-stu-id="d54d7-283">Whereas ASP.NET provides control over where state information in the <xref:System.Web.HttpContext> class is actually stored, WCF, at least in its initial version, provides no control over where extensible objects are stored.</span></span> <span data-ttu-id="d54d7-284">To představuje velmi nejlepší důvod pro výběr režimu kompatibility ASP.NET pro službu WCF.</span><span class="sxs-lookup"><span data-stu-id="d54d7-284">That constitutes the very best reason for selecting the ASP.NET compatibility mode for a WCF service.</span></span> <span data-ttu-id="d54d7-285">Pokud je konfigurovatelná konfigurace stavu nevyhnutelná a potom se rozhodnete pro režim kompatibility ASP.NET, umožní vám používat zařízení <xref:System.Web.HttpContext> třídy přesně tak, jak se používají v ASP.NET, a taky nakonfigurovat, kde se informace o stavu spravují pomocí <xref:System.Web.HttpContext> třída je uložena.</span><span class="sxs-lookup"><span data-stu-id="d54d7-285">If configurable state management is imperative, then opting for the ASP.NET compatibility mode allows you to use the facilities of the <xref:System.Web.HttpContext> class exactly as they are used in ASP.NET, and also to configure where state information managed by using the <xref:System.Web.HttpContext> class is stored.</span></span>

## <a name="security"></a><span data-ttu-id="d54d7-286">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="d54d7-286">Security</span></span>

<span data-ttu-id="d54d7-287">Možnosti zabezpečení webových služeb ASP.NET jsou ty, které slouží k zabezpečení libovolné aplikace IIS.</span><span class="sxs-lookup"><span data-stu-id="d54d7-287">The options for securing ASP.NET Web services are those for securing any IIS application.</span></span> <span data-ttu-id="d54d7-288">Vzhledem k tomu, že aplikace WCF lze hostovat nejen v rámci služby IIS, ale také v jakémkoli spustitelném souboru .NET, je nutné, aby byly možnosti pro zabezpečení aplikací WCF nezávislé na zařízeních služby IIS.</span><span class="sxs-lookup"><span data-stu-id="d54d7-288">Because WCF applications can be hosted not only within IIS but also within any .NET executable, the options for securing WCF applications must be made independent from the facilities of IIS.</span></span> <span data-ttu-id="d54d7-289">Zařízení, která jsou poskytována pro webové služby ASP.NET, jsou však k dispozici také pro služby WCF spuštěné v režimu kompatibility ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="d54d7-289">However, the facilities provided for ASP.NET Web services are also available for WCF services running in ASP.NET compatibility mode.</span></span>

### <a name="security-authentication"></a><span data-ttu-id="d54d7-290">Bezpečnost Ověřování</span><span class="sxs-lookup"><span data-stu-id="d54d7-290">Security: Authentication</span></span>

<span data-ttu-id="d54d7-291">Služba IIS poskytuje zařízení pro řízení přístupu k aplikacím, pomocí kterých můžete vybrat buď anonymní přístup, nebo různé režimy ověřování: Ověřování systému Windows, ověřování hodnotou hash, základní ověřování a ověřování .NET Passport.</span><span class="sxs-lookup"><span data-stu-id="d54d7-291">IIS provides facilities for controlling access to applications by which you can select either anonymous access or a variety of modes of authentication: Windows Authentication, Digest Authentication, Basic Authentication, and .NET Passport Authentication.</span></span> <span data-ttu-id="d54d7-292">Možnost ověřování systému Windows se dá použít k řízení přístupu k ASP.NET webovým službám.</span><span class="sxs-lookup"><span data-stu-id="d54d7-292">The Windows Authentication option can be used to control access to ASP.NET Web services.</span></span> <span data-ttu-id="d54d7-293">Pokud jsou však aplikace WCF hostovány v rámci služby IIS, je nutné nakonfigurovat službu IIS tak, aby povolovala anonymní přístup k aplikaci, aby bylo možné ověřování spravovat samotným WCF, které podporuje ověřování systému Windows mezi různými dalšími možnostmi.</span><span class="sxs-lookup"><span data-stu-id="d54d7-293">However, when WCF applications are hosted within IIS, IIS must be configured to permit anonymous access to the application, so that authentication can be managed by WCF itself, which does support Windows authentication among various other options.</span></span> <span data-ttu-id="d54d7-294">Mezi další předdefinované možnosti patří tokeny uživatelského jména, certifikáty X. 509, tokeny SAML a karta CardSpace, ale je možné definovat i vlastní mechanismy ověřování.</span><span class="sxs-lookup"><span data-stu-id="d54d7-294">The other options that are built-in include username tokens, X.509 certificates, SAML tokens, and CardSpace card, but custom authentication mechanisms can also be defined.</span></span>

### <a name="security-impersonation"></a><span data-ttu-id="d54d7-295">Bezpečnost Zosobnění</span><span class="sxs-lookup"><span data-stu-id="d54d7-295">Security: Impersonation</span></span>

<span data-ttu-id="d54d7-296">ASP.NET poskytuje prvek identity, pomocí kterého může být vytvořena webová služba ASP.NET k zosobnění konkrétního uživatele nebo pověření uživatele s aktuální žádostí.</span><span class="sxs-lookup"><span data-stu-id="d54d7-296">ASP.NET provides an identity element by which an ASP.NET Web service can be made to impersonate a particular user or whichever user’s credentials are provided with the current request.</span></span> <span data-ttu-id="d54d7-297">Tento element lze použít ke konfiguraci zosobnění v aplikacích WCF běžících v režimu kompatibility ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="d54d7-297">That element can be used to configure impersonation in WCF applications running in ASP.NET compatibility mode.</span></span>

<span data-ttu-id="d54d7-298">Konfigurační systém WCF poskytuje vlastní prvek identity pro určení konkrétního uživatele k zosobnění.</span><span class="sxs-lookup"><span data-stu-id="d54d7-298">The WCF configuration system provides its own identity element for designating a particular user to impersonate.</span></span> <span data-ttu-id="d54d7-299">Klienti a služby WCF taky můžou být pro zosobnění nezávisle nakonfigurované.</span><span class="sxs-lookup"><span data-stu-id="d54d7-299">Also, WCF clients and services can be independently configured for impersonation.</span></span> <span data-ttu-id="d54d7-300">Klienty lze nakonfigurovat k zosobnění aktuálního uživatele při odesílání požadavků.</span><span class="sxs-lookup"><span data-stu-id="d54d7-300">Clients can be configured to impersonate the current user when they transmit requests.</span></span>

```xml
<behaviors>
     <behavior name="DerivativesCalculatorClientBehavior">
      <clientCredentials>
      <windows allowedImpersonationLevel="Impersonation"/>
      </clientCredentials>
     </behavior>
</behaviors>
```

<span data-ttu-id="d54d7-301">Operace služby se dají nakonfigurovat k zosobnění přihlašovacích údajů uživatele s aktuální žádostí.</span><span class="sxs-lookup"><span data-stu-id="d54d7-301">Service operations can be configured to impersonate whichever user’s credentials are provided with the current request.</span></span>

```csharp
[OperationBehavior(Impersonation = ImpersonationOption.Required)]
public void Receive(Message input)
```

### <a name="security-authorization-using-access-control-lists"></a><span data-ttu-id="d54d7-302">Bezpečnost Ověřování pomocí Access Controlch seznamů</span><span class="sxs-lookup"><span data-stu-id="d54d7-302">Security: Authorization using Access Control Lists</span></span>

<span data-ttu-id="d54d7-303">Seznamy Access Control (ACL) lze použít k omezení přístupu k souborům. asmx.</span><span class="sxs-lookup"><span data-stu-id="d54d7-303">Access Control Lists (ACLs) can be used to restrict access to .asmx files.</span></span> <span data-ttu-id="d54d7-304">Seznamy ACL v souborech WCF. svc se ale ignorují s výjimkou v režimu kompatibility ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="d54d7-304">However, ACLs on WCF .svc files are ignored except in ASP.NET compatibility mode.</span></span>

### <a name="security-role-based-authorization"></a><span data-ttu-id="d54d7-305">Bezpečnost Autorizace na základě rolí</span><span class="sxs-lookup"><span data-stu-id="d54d7-305">Security: Role-based Authorization</span></span>

<span data-ttu-id="d54d7-306">Možnost ověřování systému Windows ve službě IIS lze použít ve spojení s elementem autorizace poskytovaným konfiguračním jazykem ASP.NET pro usnadnění ověřování na základě rolí pro webové služby ASP.NET na základě skupin systému Windows, ke kterým jsou uživatelé přiřazeni. .</span><span class="sxs-lookup"><span data-stu-id="d54d7-306">The IIS Windows Authentication option can be used in conjunction with the authorization element provided by the ASP.NET configuration language to facilitate role-based authorization for ASP.NET Web services based on the Windows groups to which users are assigned.</span></span> <span data-ttu-id="d54d7-307">ASP.NET 2,0 představil obecnější mechanizmus ověřování na základě rolí: poskytovatelé rolí.</span><span class="sxs-lookup"><span data-stu-id="d54d7-307">ASP.NET 2.0 introduced a more general role-based authorization mechanism: role providers.</span></span>

<span data-ttu-id="d54d7-308">Poskytovatelé rolí jsou třídy, které všechny implementují základní rozhraní pro dotazování na role, ke kterým je uživatel přiřazený, ale každý poskytovatel rolí ví, jak tyto informace načíst z jiného zdroje.</span><span class="sxs-lookup"><span data-stu-id="d54d7-308">Role providers are classes that all implement a basic interface for enquiring about the roles to which a user is assigned, but each role provider knows how to retrieve that information from a different source.</span></span> <span data-ttu-id="d54d7-309">ASP.NET 2,0 poskytuje poskytovatele rolí, který může načítat přiřazení rolí z databáze Microsoft SQL Server, a druhý, který může načíst přiřazení rolí z Správce autorizací systému Windows Server 2003.</span><span class="sxs-lookup"><span data-stu-id="d54d7-309">ASP.NET 2.0 provides a role provider that can retrieve role assignments from a Microsoft SQL Server database, and another that can retrieve role assignments from the Windows Server 2003 Authorization Manager.</span></span>

<span data-ttu-id="d54d7-310">Mechanismus poskytovatele rolí se dá ve skutečnosti použít nezávisle na ASP.NET v jakékoli aplikaci .NET, včetně aplikace WCF.</span><span class="sxs-lookup"><span data-stu-id="d54d7-310">The role provider mechanism can actually be used independently of ASP.NET in any .NET application, including a WCF application.</span></span> <span data-ttu-id="d54d7-311">Následující ukázková konfigurace pro aplikaci WCF ukazuje, jak je možné použít poskytovatele rolí ASP.NET jako <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>možnost vybranou prostřednictvím.</span><span class="sxs-lookup"><span data-stu-id="d54d7-311">The following sample configuration for a WCF application shows how the use of an ASP.NET role provider is an option selected by means of the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.</span></span>

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

### <a name="security-claims-based-authorization"></a><span data-ttu-id="d54d7-312">Bezpečnost Autorizace na základě rolí</span><span class="sxs-lookup"><span data-stu-id="d54d7-312">Security: Claims-based Authorization</span></span>

<span data-ttu-id="d54d7-313">Jednou z nejdůležitějších inovací služby WCF je důkladná podpora pro autorizaci přístupu k chráněným prostředkům na základě deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="d54d7-313">One of the most important innovations of WCF is its thorough support for authorizing access to protected resources based on claims.</span></span> <span data-ttu-id="d54d7-314">Deklarace identity se skládají z typu, práva a hodnoty, licence na ovladače, například.</span><span class="sxs-lookup"><span data-stu-id="d54d7-314">Claims consist of a type, a right and a value, a drivers’ license, for example.</span></span> <span data-ttu-id="d54d7-315">Poskytuje sadu deklarací identity, z nichž jeden je držitelem data narození.</span><span class="sxs-lookup"><span data-stu-id="d54d7-315">It makes a set of claims about the bearer, one of which is the bearer’s date of birth.</span></span> <span data-ttu-id="d54d7-316">Typ deklarace identity je datum narození, přičemž hodnota deklarace identity je datum narození ovladače.</span><span class="sxs-lookup"><span data-stu-id="d54d7-316">The type of that claim is date of birth, while the value of the claim is the driver’s birth date.</span></span> <span data-ttu-id="d54d7-317">Právo, které udělí nárok na nosiči, určuje, co má nosič s hodnotou deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="d54d7-317">The right that a claim confers on the bearer specifies what the bearer can do with the claim’s value.</span></span> <span data-ttu-id="d54d7-318">V případě nároku na datum narození řidiče je práva k dispozici: ovladač má toto datum narození, ale nemůže ho například změnit.</span><span class="sxs-lookup"><span data-stu-id="d54d7-318">In the case of the claim of the driver’s date of birth, the right is possession: the driver possesses that date of birth but cannot, for example, alter it.</span></span> <span data-ttu-id="d54d7-319">Ověřování založené na deklaracích obklopuje autorizaci na základě rolí, protože role představují typ deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="d54d7-319">Claims-based authorization encloses role-based authorization, because roles are a type of claim.</span></span>

<span data-ttu-id="d54d7-320">Autorizaci založenou na deklaracích je možné provést porovnáním sady deklarací s požadavky na přístup k požadavkům operace a v závislosti na výsledku tohoto porovnání, udělení nebo odepření přístupu k této operaci.</span><span class="sxs-lookup"><span data-stu-id="d54d7-320">Authorization based on claims is accomplished by comparing a set of claims to the access requirements of the operation and, depending on the outcome of that comparison, granting or denying access to the operation.</span></span> <span data-ttu-id="d54d7-321">V rámci WCF můžete určit třídu, která se má použít ke spuštění autorizace založené na deklaracích, a to znovu přiřazením hodnoty `ServiceAuthorizationManager` vlastnosti třídy <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.</span><span class="sxs-lookup"><span data-stu-id="d54d7-321">In WCF, you can specify a class to use to run claims-based authorization, once again by assigning a value to the `ServiceAuthorizationManager` property of <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.</span></span>

```xml
<behaviors>
     <behavior name='ServiceBehavior'>
     <serviceAuthorization
     serviceAuthorizationManagerType=
                   'Service.AccessChecker, Service' />
     </behavior>
</behaviors>
```

<span data-ttu-id="d54d7-322">Třídy používané ke spouštění autorizace založené na deklaracích musí být <xref:System.ServiceModel.ServiceAuthorizationManager>odvozeny z, který má pouze jednu metodu `AccessCheck()`, která má být přepsána.</span><span class="sxs-lookup"><span data-stu-id="d54d7-322">Classes used to run claims-based authorization must derive from <xref:System.ServiceModel.ServiceAuthorizationManager>, which has just one method to override, `AccessCheck()`.</span></span> <span data-ttu-id="d54d7-323">Služba WCF volá tuto metodu vždy, když je vyvolána operace služby a poskytuje <xref:System.ServiceModel.OperationContext> objekt, který má deklarace pro uživatele ve své `ServiceSecurityContext.AuthorizationContext` vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="d54d7-323">WCF calls that method whenever an operation of the service is invoked and provides a <xref:System.ServiceModel.OperationContext> object, which has the claims for the user in its `ServiceSecurityContext.AuthorizationContext` property.</span></span> <span data-ttu-id="d54d7-324">WCF provádí sestavování deklarací identity uživatele z libovolného tokenu zabezpečení, který uživatel zadal pro ověřování, což ponechá úkol vyhodnotit, zda tyto deklarace pro danou operaci postačují.</span><span class="sxs-lookup"><span data-stu-id="d54d7-324">WCF does the work of assembling claims about the user from whatever security token the user provided for authentication, which leaves the of task of evaluating whether those claims suffice for the operation in question.</span></span>

<span data-ttu-id="d54d7-325">Tato technologie WCF automaticky sestavuje deklarace z jakéhokoli typu tokenu zabezpečení, protože způsobuje autorizaci kódu na základě deklarace zcela nezávisle na ověřovacím mechanismu.</span><span class="sxs-lookup"><span data-stu-id="d54d7-325">That WCF automatically assembles claims from any kind of security token is a highly significant innovation, because it makes the code for authorization based on the claims entirely independent of the authentication mechanism.</span></span> <span data-ttu-id="d54d7-326">Naproti tomu autorizace pomocí seznamů ACL nebo rolí v ASP.NET je úzce spjata s ověřováním systému Windows.</span><span class="sxs-lookup"><span data-stu-id="d54d7-326">By contrast, authorization using ACLs or roles in ASP.NET is closely tied to Windows authentication.</span></span>

### <a name="security-confidentiality"></a><span data-ttu-id="d54d7-327">Bezpečnost Chovávat</span><span class="sxs-lookup"><span data-stu-id="d54d7-327">Security: Confidentiality</span></span>

<span data-ttu-id="d54d7-328">Důvěrnost zpráv vyměňovaných s ASP.NET webovými službami se dá zajistit na úrovni přenosu tím, že v rámci služby IIS nakonfigurujete aplikaci tak, aby používala protokol HTTPS (Secure Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="d54d7-328">The confidentiality of messages exchanged with ASP.NET Web services can be ensured at the transport level by configuring the application within IIS to use the Secure Hypertext Transfer Protocol (HTTPS).</span></span> <span data-ttu-id="d54d7-329">Totéž lze provést pro aplikace WCF hostované v rámci služby IIS.</span><span class="sxs-lookup"><span data-stu-id="d54d7-329">The same can be done for WCF applications hosted within IIS.</span></span> <span data-ttu-id="d54d7-330">Aplikace WCF hostované mimo službu IIS ale můžou být nakonfigurované tak, aby používaly zabezpečený transportní protokol.</span><span class="sxs-lookup"><span data-stu-id="d54d7-330">However, WCF applications hosted outside of IIS can also be configured to use a secure transport protocol.</span></span> <span data-ttu-id="d54d7-331">Důležitější je, že aplikace WCF je taky možné nakonfigurovat tak, aby se zprávy před jejich přečtením používaly pomocí protokolu WS-Security.</span><span class="sxs-lookup"><span data-stu-id="d54d7-331">More important, WCF applications can also be configured to secure the messages before they are transported, using the WS-Security protocol.</span></span> <span data-ttu-id="d54d7-332">Zabezpečení pouze těla zprávy pomocí WS-Security umožňuje, aby je bylo možné před dosažením konečného cíle přenést do všech dodavatelů.</span><span class="sxs-lookup"><span data-stu-id="d54d7-332">Securing just the body of a message using WS-Security allows it to be transmitted confidentially across intermediaries before reaching its final destination.</span></span>

## <a name="globalization"></a><span data-ttu-id="d54d7-333">Globalizace</span><span class="sxs-lookup"><span data-stu-id="d54d7-333">Globalization</span></span>

<span data-ttu-id="d54d7-334">Jazyk konfigurace ASP.NET umožňuje zadat jazykovou verzi pro jednotlivé služby.</span><span class="sxs-lookup"><span data-stu-id="d54d7-334">The ASP.NET configuration language allows you to specify the culture for individual services.</span></span> <span data-ttu-id="d54d7-335">WCF nepodporuje toto nastavení konfigurace, s výjimkou v režimu kompatibility ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="d54d7-335">The WCF does not support that configuration setting except in ASP.NET compatibility mode.</span></span> <span data-ttu-id="d54d7-336">Chcete-li lokalizovat službu WCF, která nepoužívá režim kompatibility ASP.NET, zkompilujte typ služby do sestavení specifických pro jazykovou verzi a pro každé sestavení specifické pro jazykovou verzi použijte samostatné koncové body specifické pro jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="d54d7-336">To localize a WCF service that does not use ASP.NET compatibility mode, compile the service type into culture-specific assemblies, and have separate culture-specific endpoints for each culture-specific assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="d54d7-337">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d54d7-337">See also</span></span>

- [<span data-ttu-id="d54d7-338">Porovnání webových služeb ASP.NET se službou WCF na základě účelu a používaných standardů</span><span class="sxs-lookup"><span data-stu-id="d54d7-338">Comparing ASP.NET Web Services to WCF Based on Purpose and Standards Used</span></span>](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used.md)
