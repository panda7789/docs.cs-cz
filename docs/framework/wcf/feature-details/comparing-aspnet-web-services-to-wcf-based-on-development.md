---
title: Porovnání webových služeb ASP.NET Web Services s technologií WCF z hlediska vývojových požadavků
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f362d00e-ce82-484f-9d4f-27e579d5c320
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8e60d28314c47907cc825871b88a0dc771cd0511
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2018
---
# <a name="comparing-aspnet-web-services-to-wcf-based-on-development"></a><span data-ttu-id="6264e-102">Porovnání webových služeb ASP.NET Web Services s technologií WCF z hlediska vývojových požadavků</span><span class="sxs-lookup"><span data-stu-id="6264e-102">Comparing ASP.NET Web Services to WCF Based on Development</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="6264e-103"> má možnost režim kompatibility ASP.NET povolit [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace pro naprogramovaný tak a konfiguraci jako webových služeb ASP.NET a napodobovat jejich chování.</span><span class="sxs-lookup"><span data-stu-id="6264e-103"> has an ASP.NET compatibility mode option to enable [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications to be programmed and configured like ASP.NET Web services, and mimic their behavior.</span></span> <span data-ttu-id="6264e-104">V následujících částech porovnání webových služeb ASP.NET a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] podle co je potřeba k vývoji aplikací pomocí obou technologií.</span><span class="sxs-lookup"><span data-stu-id="6264e-104">The following sections compare ASP.NET Web services and [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] based on what is required to develop applications using both technologies.</span></span>  
  
## <a name="data-representation"></a><span data-ttu-id="6264e-105">Reprezentace dat</span><span class="sxs-lookup"><span data-stu-id="6264e-105">Data Representation</span></span>  
 <span data-ttu-id="6264e-106">Vývoj webové služby pomocí ASP.NET se obvykle začíná definování všechny rozšířené datové typy, které má používat služba.</span><span class="sxs-lookup"><span data-stu-id="6264e-106">The development of a Web service with ASP.NET typically begins with defining any complex data types the service is to use.</span></span> <span data-ttu-id="6264e-107">ASP.NET spoléhá na <xref:System.Xml.Serialization.XmlSerializer> přeložit data reprezentována rozhraní .NET Framework typů XML pro přenos do nebo ze služby a překládat data přijatá ve formátu XML do objekty rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6264e-107">ASP.NET relies on the <xref:System.Xml.Serialization.XmlSerializer> to translate data represented by .NET Framework types to XML for transmission to or from a service and to translate data received as XML into .NET Framework objects.</span></span> <span data-ttu-id="6264e-108">Definování komplexních datové typy, které je použití služby ASP.NET vyžaduje třídy definici rozhraní .NET Framework, který <xref:System.Xml.Serialization.XmlSerializer> může serializovat do a z XML.</span><span class="sxs-lookup"><span data-stu-id="6264e-108">Defining the complex data types that an ASP.NET service is to use requires the definition of .NET Framework classes that the <xref:System.Xml.Serialization.XmlSerializer> can serialize to and from XML.</span></span> <span data-ttu-id="6264e-109">Těchto tříd lze zapsat ručně, nebo vytvořit z definice typů ve schématu XML pomocí příkazového řádku XML schémata a datových typů podporu nástroji pro xsd.exe.</span><span class="sxs-lookup"><span data-stu-id="6264e-109">Such classes can be written manually, or generated from definitions of the types in XML Schema using the command-line XML Schemas/Data Types Support Utility, xsd.exe.</span></span>  
  
 <span data-ttu-id="6264e-110">Následuje seznam klíčů problémů vědět při definování rozhraní .NET Framework třída, která je <xref:System.Xml.Serialization.XmlSerializer> může serializovat do a z XML:</span><span class="sxs-lookup"><span data-stu-id="6264e-110">The following is a list of key issues to know when defining .NET Framework classes that the <xref:System.Xml.Serialization.XmlSerializer> can serialize to and from XML:</span></span>  
  
-   <span data-ttu-id="6264e-111">Veřejná pole a vlastnosti objektů rozhraní .NET Framework se přeložit na XML.</span><span class="sxs-lookup"><span data-stu-id="6264e-111">Only the public fields and properties of .NET Framework objects are translated into XML.</span></span>  
  
-   <span data-ttu-id="6264e-112">Instance třídy kolekce můžete serializován do souboru XML, pouze v případě, že třídy implementovat buď <xref:System.Collections.IEnumerable> nebo <xref:System.Collections.ICollection> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6264e-112">Instances of collection classes can be serialized into XML only if the classes implement either the <xref:System.Collections.IEnumerable> or <xref:System.Collections.ICollection> interface.</span></span>  
  
-   <span data-ttu-id="6264e-113">Třídy implementující <xref:System.Collections.IDictionary> rozhraní, jako například <xref:System.Collections.Hashtable>, nesmí být serializován do souboru XML.</span><span class="sxs-lookup"><span data-stu-id="6264e-113">Classes that implement the <xref:System.Collections.IDictionary> interface, such as <xref:System.Collections.Hashtable>, cannot be serialized into XML.</span></span>  
  
-   <span data-ttu-id="6264e-114">Dobře mnoho typů v atributu <xref:System.Xml.Serialization> oboru názvů lze přidat do třídy rozhraní .NET Framework a její členy k řízení zastoupení instancí třídy ve formátu XML.</span><span class="sxs-lookup"><span data-stu-id="6264e-114">The great many attribute types in the <xref:System.Xml.Serialization> namespace can be added to a .NET Framework class and its members to control how instances of the class are represented in XML.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="6264e-115"> vývoj aplikací obvykle také začíná definici komplexních typů.</span><span class="sxs-lookup"><span data-stu-id="6264e-115"> application development usually also begins with the definition of complex types.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="6264e-116"> lze používat stejné typy rozhraní .NET Framework jako webové služby ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="6264e-116"> can be made to use the same .NET Framework types as ASP.NET Web services.</span></span>  
  
 <span data-ttu-id="6264e-117">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] <xref:System.Runtime.Serialization.DataContractAttribute> a <xref:System.Runtime.Serialization.DataMemberAttribute> lze přidat na rozhraní .NET Framework typy, které určují, že instance typu se k serializaci do XML a které konkrétní pole nebo vlastnosti typu se k serializaci, jak znázorňuje následující ukázka kód.</span><span class="sxs-lookup"><span data-stu-id="6264e-117">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> can be added to .NET Framework types to indicate that instances of the type are to be serialized into XML, and which particular fields or properties of the type are to be serialized, as shown in the following sample code.</span></span>  
  
```  
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
  
 <span data-ttu-id="6264e-118"><xref:System.Runtime.Serialization.DataContractAttribute> Označuje, že nulový nebo nenulový počet typ pole nebo vlastnosti mají být serializován, při <xref:System.Runtime.Serialization.DataMemberAttribute> označuje, že pole nebo vlastnost je k serializaci.</span><span class="sxs-lookup"><span data-stu-id="6264e-118">The <xref:System.Runtime.Serialization.DataContractAttribute> signifies that zero or more of a type’s fields or properties are to be serialized, while the <xref:System.Runtime.Serialization.DataMemberAttribute> indicates that a particular field or property is to be serialized.</span></span> <span data-ttu-id="6264e-119"><xref:System.Runtime.Serialization.DataContractAttribute> Lze použít ke třídě nebo struktuře.</span><span class="sxs-lookup"><span data-stu-id="6264e-119">The <xref:System.Runtime.Serialization.DataContractAttribute> can be applied to a class or structure.</span></span> <span data-ttu-id="6264e-120"><xref:System.Runtime.Serialization.DataMemberAttribute> Můžete použít pro pole nebo vlastnost a pole a vlastnosti, na které se použije atribut může být veřejné nebo soukromé.</span><span class="sxs-lookup"><span data-stu-id="6264e-120">The <xref:System.Runtime.Serialization.DataMemberAttribute> can be applied to a field or a property, and the fields and properties to which the attribute is applied can be either public or private.</span></span> <span data-ttu-id="6264e-121">Instance typy, které mají <xref:System.Runtime.Serialization.DataContractAttribute> u nich se označuje jako měnící data [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6264e-121">Instances of types that have the <xref:System.Runtime.Serialization.DataContractAttribute> applied to them are referred to as data contracts in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="6264e-122">Jsou serializován do souboru XML pomocí <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="6264e-122">They are serialized into XML using <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="6264e-123">Tady je seznam důležitých rozdílů mezi použitím <xref:System.Runtime.Serialization.DataContractSerializer> a pomocí <xref:System.Xml.Serialization.XmlSerializer> a různé atributy <xref:System.Xml.Serialization> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="6264e-123">The following is a list of the important differences between using the <xref:System.Runtime.Serialization.DataContractSerializer> and using the <xref:System.Xml.Serialization.XmlSerializer> and the various attributes of the <xref:System.Xml.Serialization> namespace.</span></span>  
  
-   <span data-ttu-id="6264e-124"><xref:System.Xml.Serialization.XmlSerializer> a atributy <xref:System.Xml.Serialization> obor názvů jsou navržené tak, abyste mohli k mapování typů rozhraní .NET Framework na libovolný platný typ definovaná ve schématu XML, a proto poskytují velmi přesné kontrolu nad zastoupení typu v kódu XML.</span><span class="sxs-lookup"><span data-stu-id="6264e-124">The <xref:System.Xml.Serialization.XmlSerializer> and the attributes of the <xref:System.Xml.Serialization> namespace are designed to allow you to map .NET Framework types to any valid type defined in XML Schema, and so they provide for very precise control over how a type is represented in XML.</span></span> <span data-ttu-id="6264e-125"><xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.DataContractAttribute> a <xref:System.Runtime.Serialization.DataMemberAttribute> poskytují velmi malé kontrolu nad zastoupení typu v kódu XML.</span><span class="sxs-lookup"><span data-stu-id="6264e-125">The <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> provide very little control over how a type is represented in XML.</span></span> <span data-ttu-id="6264e-126">Můžete zadat pouze obory názvů a názvy používá k reprezentování typ a příslušné pole a vlastnosti v souboru XML a pořadí, ve kterém polí a vlastností zobrazí v souboru XML:</span><span class="sxs-lookup"><span data-stu-id="6264e-126">You can only specify the namespaces and names used to represent the type and its fields or properties in the XML, and the sequence in which the fields and properties appear in the XML:</span></span>  
  
    ```  
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
  
     <span data-ttu-id="6264e-127">Všem ostatním o struktuře XML, který představuje typ rozhraní .NET je dáno <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="6264e-127">Everything else about the structure of the XML used to represent the .NET type is determined by the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
-   <span data-ttu-id="6264e-128">Díky tomu, že není možností řízení jak typu je možné vyjádřit v XML, stane vysoce předvídatelný pro proces serializace <xref:System.Runtime.Serialization.DataContractSerializer>a tím, snazší za účelem optimalizace.</span><span class="sxs-lookup"><span data-stu-id="6264e-128">By not permitting much control over how a type is to be represented in XML, the serialization process becomes highly predictable for the <xref:System.Runtime.Serialization.DataContractSerializer>, and, thereby, easier to optimize.</span></span> <span data-ttu-id="6264e-129">Praktické výhodou návrh <xref:System.Runtime.Serialization.DataContractSerializer> je lepší výkon, přibližně deset procent lepší výkon.</span><span class="sxs-lookup"><span data-stu-id="6264e-129">A practical benefit of the design of the <xref:System.Runtime.Serialization.DataContractSerializer> is better performance, approximately ten percent better performance.</span></span>  
  
-   <span data-ttu-id="6264e-130">Atributy pro použití s <xref:System.Xml.Serialization.XmlSerializer> neoznačují které pole nebo vlastnosti typu se serializován do souboru XML, zatímco <xref:System.Runtime.Serialization.DataMemberAttribute> pro použití s <xref:System.Runtime.Serialization.DataContractSerializer> explicitně zobrazuje vlastnosti nebo pole, které se serializují.</span><span class="sxs-lookup"><span data-stu-id="6264e-130">The attributes for use with the <xref:System.Xml.Serialization.XmlSerializer> do not indicate which fields or properties of the type are serialized into XML, whereas the <xref:System.Runtime.Serialization.DataMemberAttribute> for use with the <xref:System.Runtime.Serialization.DataContractSerializer> shows explicitly which fields or properties are serialized.</span></span> <span data-ttu-id="6264e-131">Kontrakty dat jsou proto explicitní kontrakty o struktuře data, která aplikace je k odesílání a příjmu.</span><span class="sxs-lookup"><span data-stu-id="6264e-131">Therefore, data contracts are explicit contracts about the structure of the data that an application is to send and receive.</span></span>  
  
-   <span data-ttu-id="6264e-132"><xref:System.Xml.Serialization.XmlSerializer> Může překládat pouze veřejné členy objektu .NET do souboru XML, <xref:System.Runtime.Serialization.DataContractSerializer> může překládat členy objektů do souboru XML bez ohledu na to modifikátory přístupu těchto členů.</span><span class="sxs-lookup"><span data-stu-id="6264e-132">The <xref:System.Xml.Serialization.XmlSerializer> can only translate the public members of a .NET object into XML, the <xref:System.Runtime.Serialization.DataContractSerializer> can translate the members of objects into XML regardless of the access modifiers of those members.</span></span>  
  
-   <span data-ttu-id="6264e-133">V důsledku schopnost serializovat neveřejným členy typy do souboru XML, <xref:System.Runtime.Serialization.DataContractSerializer> má méně omezení pro různé typy .NET, které mohou serializovat do souboru XML.</span><span class="sxs-lookup"><span data-stu-id="6264e-133">As a consequence of being able to serialize the non-public members of types into XML, the <xref:System.Runtime.Serialization.DataContractSerializer> has fewer restrictions on the variety of .NET types that it can serialize into XML.</span></span> <span data-ttu-id="6264e-134">Konkrétně může překládat do typy XML jako <xref:System.Collections.Hashtable> implementující <xref:System.Collections.IDictionary> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6264e-134">In particular, it can translate into XML types like <xref:System.Collections.Hashtable> that implement the <xref:System.Collections.IDictionary> interface.</span></span> <span data-ttu-id="6264e-135"><xref:System.Runtime.Serialization.DataContractSerializer> Je mnohem pravděpodobnější mohli k serializaci instancí všechny existující typ formátu .NET do XML bez nutnosti upravte definici typu nebo vývoj obálku pro ni.</span><span class="sxs-lookup"><span data-stu-id="6264e-135">The <xref:System.Runtime.Serialization.DataContractSerializer> is much more likely to be able to serialize the instances of any pre-existing .NET type into XML without having to either modify the definition of the type or develop a wrapper for it.</span></span>  
  
-   <span data-ttu-id="6264e-136">Jiné důsledkem <xref:System.Runtime.Serialization.DataContractSerializer> nebudete mít přístup k neveřejným členy typu je, že vyžaduje úplný vztah důvěryhodnosti, zatímco <xref:System.Xml.Serialization.XmlSerializer> neexistuje.</span><span class="sxs-lookup"><span data-stu-id="6264e-136">Another consequence of the <xref:System.Runtime.Serialization.DataContractSerializer> being able to access the non-public members of a type is that it requires full trust, whereas the <xref:System.Xml.Serialization.XmlSerializer> does not.</span></span> <span data-ttu-id="6264e-137">Oprávnění úplný vztah důvěryhodnosti k kódu poskytuje úplný přístup ke všem prostředkům na počítači, který je přístupný pomocí přihlašovacích údajů, za kterých je prováděna kód.</span><span class="sxs-lookup"><span data-stu-id="6264e-137">The Full Trust code access permission gives complete access to all resources on a machine that can be accessed using the credentials under which the code is executing.</span></span> <span data-ttu-id="6264e-138">Tato možnost by měla použít dát pozor, jako plně důvěryhodný kód přistupuje k všechny prostředky ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="6264e-138">This option should be used with care as fully trusted code accesses all resources on your machine.</span></span>  
  
-   <span data-ttu-id="6264e-139"><xref:System.Runtime.Serialization.DataContractSerializer> Zahrnuje některé podporu pro správu verzí:</span><span class="sxs-lookup"><span data-stu-id="6264e-139">The <xref:System.Runtime.Serialization.DataContractSerializer> incorporates some support for versioning:</span></span>  
  
    -   <span data-ttu-id="6264e-140"><xref:System.Runtime.Serialization.DataMemberAttribute> Má <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> vlastnost, která může být přiřazena hodnota false pro členy, které jsou přidány do nové verze kontraktu dat, které nebyly v dřívějších verzích, a tím povolíte aplikací s novější verzí kontrakt jako schopna zpracovat starší verze.</span><span class="sxs-lookup"><span data-stu-id="6264e-140">The <xref:System.Runtime.Serialization.DataMemberAttribute> has an <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> property that can be assigned a value of false for members that are added to new versions of a data contract that were not present in earlier versions, thereby allowing applications with the newer version of the contract to be able to process earlier versions.</span></span>  
  
    -   <span data-ttu-id="6264e-141">Tak, že kontraktu dat implementovat <xref:System.Runtime.Serialization.IExtensibleDataObject> rozhraní, jeden můžete povolit <xref:System.Runtime.Serialization.DataContractSerializer> předat členy definované v novější verze sady kontraktu dat prostřednictvím aplikací s předchozími verzemi smlouvy.</span><span class="sxs-lookup"><span data-stu-id="6264e-141">By having a data contract implement the <xref:System.Runtime.Serialization.IExtensibleDataObject> interface, one can allow the <xref:System.Runtime.Serialization.DataContractSerializer> to pass members defined in newer versions of a data contract through applications with earlier versions of the contract.</span></span>  
  
 <span data-ttu-id="6264e-142">I přes všechny rozdíly, XML, do kterého <xref:System.Xml.Serialization.XmlSerializer> serializuje typu ve výchozím nastavení je sémanticky stejný jako soubor XML, do kterého <xref:System.Runtime.Serialization.DataContractSerializer> serializuje typu zadaný obor názvů pro soubor XML byl explicitně definován.</span><span class="sxs-lookup"><span data-stu-id="6264e-142">Despite all of the differences, the XML into which the <xref:System.Xml.Serialization.XmlSerializer> serializes a type by default is semantically identical to the XML into which the <xref:System.Runtime.Serialization.DataContractSerializer> serializes a type, provided the namespace for the XML is explicitly defined.</span></span> <span data-ttu-id="6264e-143">Následující třídy, která má atributy pro použití s oběma serializátorů, je přeložit na sémanticky identické XML pomocí <xref:System.Xml.Serialization.XmlSerializer> a <xref:System.Runtime.Serialization.DataContractAttribute>:</span><span class="sxs-lookup"><span data-stu-id="6264e-143">The following class, which has attributes for use with both of the serializers, is translated into semantically identical XML by the <xref:System.Xml.Serialization.XmlSerializer> and by the <xref:System.Runtime.Serialization.DataContractAttribute>:</span></span>  
  
```  
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
  
 <span data-ttu-id="6264e-144">Windows software development kit (SDK) zahrnuje nástroj příkazového řádku volat [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="6264e-144">The Windows software development kit (SDK) includes a command-line tool called the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="6264e-145">Nástroj xsd.exe použít s webovými službami ASP.NET, jako například Svcutil.exe může generovat definice datových typů .NET ze schématu XML.</span><span class="sxs-lookup"><span data-stu-id="6264e-145">Like the xsd.exe tool used with ASP.NET Web services, Svcutil.exe can generate definitions of .NET data types from XML Schema.</span></span> <span data-ttu-id="6264e-146">Typy jsou kontrakty dat, pokud <xref:System.Runtime.Serialization.DataContractSerializer> můžete emitování XML ve formátu XML schéma definované; jinak, jsou určené pro použití serializace <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="6264e-146">The types are data contracts if the <xref:System.Runtime.Serialization.DataContractSerializer> can emit XML in the format defined by the XML Schema; otherwise, they are intended for serialization using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="6264e-147">Svcutil.exe může také generovat schéma XML z kontrakty dat pomocí jeho `dataContractOnly` přepínače.</span><span class="sxs-lookup"><span data-stu-id="6264e-147">Svcutil.exe can also generate an XML schema from data contracts by using its `dataContractOnly` switch.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6264e-148">I když webových služeb ASP.NET použijte <xref:System.Xml.Serialization.XmlSerializer>, a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] režim kompatibility ASP.NET umožňuje [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby napodobují chování webových služeb ASP.NET, možnost kompatibility ASP.NET neomezuje jeden pomocí <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="6264e-148">Although ASP.NET Web services use the <xref:System.Xml.Serialization.XmlSerializer>, and [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ASP.NET compatibility mode makes [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services mimic the behavior of ASP.NET Web services, the ASP.NET compatibility option does not restrict one to using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="6264e-149">Stále můžete použít <xref:System.Runtime.Serialization.DataContractSerializer> do služeb spuštěných v režimu kompatibility ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="6264e-149">One can still use the <xref:System.Runtime.Serialization.DataContractSerializer> with services running in the ASP.NET compatibility mode.</span></span>  
  
## <a name="service-development"></a><span data-ttu-id="6264e-150">Vývoj pro služby</span><span class="sxs-lookup"><span data-stu-id="6264e-150">Service Development</span></span>  
 <span data-ttu-id="6264e-151">K vývoji služby pomocí ASP.NET, byla obvyklé přidat <xref:System.Web.Services.WebService> atribut na třídu a <xref:System.Web.Services.WebMethodAttribute> na některou z metod této třídy, které mají být operace služby:</span><span class="sxs-lookup"><span data-stu-id="6264e-151">To develop a service using ASP.NET, it has been customary to add the <xref:System.Web.Services.WebService> attribute to a class, and the <xref:System.Web.Services.WebMethodAttribute> to any of that class’ methods that are to be operations of the service:</span></span>  
  
```  
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
  
 <span data-ttu-id="6264e-152">ASP.NET 2.0 zavedla možnost přidání atributu <xref:System.Web.Services.WebService> a <xref:System.Web.Services.WebMethodAttribute> rozhraní, nikoli třída a zápis třídu pro implementaci rozhraní:</span><span class="sxs-lookup"><span data-stu-id="6264e-152">ASP.NET 2.0 introduced the option of adding the attribute <xref:System.Web.Services.WebService> and <xref:System.Web.Services.WebMethodAttribute> to an interface rather than to a class, and writing a class to implement the interface:</span></span>  
  
```  
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
  
 <span data-ttu-id="6264e-153">Tato možnost je jako upřednostňované, protože rozhraní s <xref:System.Web.Services.WebService> atribut se považuje za kontraktu pro operace prováděné na službu, kterou lze opětovně použít s různými třídami, které může implementovat stejné kontraktu různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="6264e-153">Using this option is to be preferred, because the interface with the <xref:System.Web.Services.WebService> attribute constitutes a contract for the operations performed by the service that can be reused with various classes that might implement that same contract in different ways.</span></span>  
  
 <span data-ttu-id="6264e-154">A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] je služba poskytovaná tak, že definujete jeden nebo více [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] koncové body.</span><span class="sxs-lookup"><span data-stu-id="6264e-154">A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service is provided by defining one or more [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoints.</span></span> <span data-ttu-id="6264e-155">Koncový bod je definována adresy, vazby a kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="6264e-155">An endpoint is defined by an address, a binding and a service contract.</span></span> <span data-ttu-id="6264e-156">Adresa definuje, kde se služba nachází.</span><span class="sxs-lookup"><span data-stu-id="6264e-156">The address defines where the service is located.</span></span> <span data-ttu-id="6264e-157">Vazba Určuje, jak se komunikovat se službou.</span><span class="sxs-lookup"><span data-stu-id="6264e-157">The binding specifies how to communicate with the service.</span></span> <span data-ttu-id="6264e-158">Kontrakt služby definuje operace, které můžete provádět službu.</span><span class="sxs-lookup"><span data-stu-id="6264e-158">The service contract defines the operations that the service can perform.</span></span>  
  
 <span data-ttu-id="6264e-159">Kontrakt služby je obvykle definováno nejprve přidáním <xref:System.ServiceModel.ServiceContractAttribute> a <xref:System.ServiceModel.OperationContractAttribute> k rozhraní:</span><span class="sxs-lookup"><span data-stu-id="6264e-159">The service contract is usually defined first, by adding <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> to an interface:</span></span>  
  
```  
[ServiceContract]  
public interface IEcho  
{  
     [OperationContract]  
     string Echo(string input);  
}  
```  
  
 <span data-ttu-id="6264e-160"><xref:System.ServiceModel.ServiceContractAttribute> Určuje, že definuje rozhraní [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kontrakt služby a <xref:System.ServiceModel.OperationContractAttribute> označuje, která, pokud existuje, metod rozhraní definuje operace kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="6264e-160">The <xref:System.ServiceModel.ServiceContractAttribute> specifies that the interface defines a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service contract, and the <xref:System.ServiceModel.OperationContractAttribute> indicates which, if any, of the methods of the interface define operations of the service contract.</span></span>  
  
 <span data-ttu-id="6264e-161">Po definování kontraktu služby, je implementována ve třídě, tak, že třída implementovat rozhraní, ve které je definováno kontrakt služby:</span><span class="sxs-lookup"><span data-stu-id="6264e-161">Once a service contract has been defined, it is implemented in a class, by having the class implement the interface by which the service contract is defined:</span></span>  
  
```  
public class Service : IEcho  
{  
    public string Echo(string input)  
    {  
       return input;  
    }  
}  
```  
  
 <span data-ttu-id="6264e-162">Třídu, která implementuje kontraktu služby se označuje jako typ služby v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6264e-162">A class that implements a service contract is referred to as a service type in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 <span data-ttu-id="6264e-163">Dalším krokem je adresu a vazbu přidružit typ služby.</span><span class="sxs-lookup"><span data-stu-id="6264e-163">The next step is to associate an address and a binding with a service type.</span></span> <span data-ttu-id="6264e-164">Se obvykle provádí v konfiguračním souboru buď úpravou souboru přímo, nebo v editoru konfigurace součástí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6264e-164">That is typically done in a configuration file, either by editing the file directly, or by using a configuration editor provided with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="6264e-165">Tady je příklad konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="6264e-165">Here is an example of a configuration file.</span></span>  
  
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
  
 <span data-ttu-id="6264e-166">Vazba určuje sadu protokolů pro komunikaci s aplikací.</span><span class="sxs-lookup"><span data-stu-id="6264e-166">The binding specifies the set of protocols for communicating with the application.</span></span> <span data-ttu-id="6264e-167">Následující tabulka uvádí vazby poskytované systémem, které reprezentují běžné možnosti.</span><span class="sxs-lookup"><span data-stu-id="6264e-167">The following table lists the system-provided bindings that represent common options.</span></span>  
  
|<span data-ttu-id="6264e-168">Název</span><span class="sxs-lookup"><span data-stu-id="6264e-168">Name</span></span>|<span data-ttu-id="6264e-169">Účel</span><span class="sxs-lookup"><span data-stu-id="6264e-169">Purpose</span></span>|  
|----------|-------------|  
|<span data-ttu-id="6264e-170">BasicHttpBinding</span><span class="sxs-lookup"><span data-stu-id="6264e-170">BasicHttpBinding</span></span>|<span data-ttu-id="6264e-171">Vzájemná funkční spolupráce s webovými službami a podpůrné služby WS-BasicProfile 1.1 a 1.0 profil základní zabezpečení klientů.</span><span class="sxs-lookup"><span data-stu-id="6264e-171">Interoperability with Web services and clients supporting the WS-BasicProfile 1.1 and Basic Security Profile 1.0.</span></span>|  
|<span data-ttu-id="6264e-172">WSHttpBinding</span><span class="sxs-lookup"><span data-stu-id="6264e-172">WSHttpBinding</span></span>|<span data-ttu-id="6264e-173">Vzájemná funkční spolupráce s webovými službami a klienty, kteří podporují WS-\* protokoly prostřednictvím protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="6264e-173">Interoperability with Web services and clients that support the WS-\* protocols over HTTP.</span></span>|  
|<span data-ttu-id="6264e-174">WSDualHttpBinding</span><span class="sxs-lookup"><span data-stu-id="6264e-174">WSDualHttpBinding</span></span>|<span data-ttu-id="6264e-175">Duplexní komunikaci pomocí protokolu HTTP, podle kterého příjemce úvodní zpráva není odpověď přímo do počáteční odesílatele, ale může přenášet libovolný počet odpovědi přes v časovém intervalu pomocí protokolu HTTP v souladu s WS-\* protokoly.</span><span class="sxs-lookup"><span data-stu-id="6264e-175">Duplex HTTP communication, by which the receiver of an initial message does not reply directly to the initial sender, but may transmit any number of responses over a period of time by using HTTP in conformity with WS-\* protocols.</span></span>|  
|<span data-ttu-id="6264e-176">Wsfederationbinding –</span><span class="sxs-lookup"><span data-stu-id="6264e-176">WSFederationBinding</span></span>|<span data-ttu-id="6264e-177">Komunikaci pomocí protokolu HTTP, ve kterém lze řídit přístup k prostředkům služby založené na přihlašovací údaje vystavený poskytovatele explicitně identifikovat přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="6264e-177">HTTP communication, in which access to the resources of a service can be controlled based on credentials issued by an explicitly-identified credential provider.</span></span>|  
|<span data-ttu-id="6264e-178">NetTcpBinding</span><span class="sxs-lookup"><span data-stu-id="6264e-178">NetTcpBinding</span></span>|<span data-ttu-id="6264e-179">Bezpečná a spolehlivá, vysoce výkonných komunikace mezi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] softwaru entity v síti.</span><span class="sxs-lookup"><span data-stu-id="6264e-179">Secure, reliable, high-performance communication between [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] software entities across a network.</span></span>|  
|<span data-ttu-id="6264e-180">NetNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="6264e-180">NetNamedPipeBinding</span></span>|<span data-ttu-id="6264e-181">Bezpečná a spolehlivá, vysoce výkonných komunikace mezi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] softwaru entity na stejném počítači.</span><span class="sxs-lookup"><span data-stu-id="6264e-181">Secure, reliable, high-performance communication between [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] software entities on the same machine.</span></span>|  
|<span data-ttu-id="6264e-182">– NetMsmqBinding</span><span class="sxs-lookup"><span data-stu-id="6264e-182">NetMsmqBinding</span></span>|<span data-ttu-id="6264e-183">Komunikace mezi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] entity softwaru pomocí služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="6264e-183">Communication between [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] software entities by using MSMQ.</span></span>|  
|<span data-ttu-id="6264e-184">MsmqIntegrationBinding</span><span class="sxs-lookup"><span data-stu-id="6264e-184">MsmqIntegrationBinding</span></span>|<span data-ttu-id="6264e-185">Komunikace mezi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] softwaru entitu a jinou entitou softwaru pomocí služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="6264e-185">Communication between a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] software entity and another software entity by using MSMQ.</span></span>|  
|<span data-ttu-id="6264e-186">NetPeerTcpBinding</span><span class="sxs-lookup"><span data-stu-id="6264e-186">NetPeerTcpBinding</span></span>|<span data-ttu-id="6264e-187">Komunikace mezi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] entity softwaru pomocí sítě Windows Peer-to-Peer.</span><span class="sxs-lookup"><span data-stu-id="6264e-187">Communication between [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] software entities by using Windows Peer-to-Peer Networking.</span></span>|  
  
 <span data-ttu-id="6264e-188">Vazby poskytované systémem <xref:System.ServiceModel.BasicHttpBinding>, zahrnuje sadu protokolů podporovaných webových služeb ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="6264e-188">The system-provided binding, <xref:System.ServiceModel.BasicHttpBinding>, incorporates the set of protocols supported by ASP.NET Web services.</span></span>  
  
 <span data-ttu-id="6264e-189">Vlastní vazby pro [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace jsou snadno definována jako kolekce prvku vazby třídy, která [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] používá k implementaci jednotlivých protokolů.</span><span class="sxs-lookup"><span data-stu-id="6264e-189">Custom bindings for [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications are easily defined as collections of the binding element classes that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses to implement individual protocols.</span></span> <span data-ttu-id="6264e-190">Nové prvky vazby je možné zapsat do představují další protokoly.</span><span class="sxs-lookup"><span data-stu-id="6264e-190">New binding elements can be written to represent additional protocols.</span></span>  
  
 <span data-ttu-id="6264e-191">Interní chování typů služeb lze upravit pomocí vlastností rodiny třídy názvem chování.</span><span class="sxs-lookup"><span data-stu-id="6264e-191">The internal behavior of service types can be adjusted using the properties of a family of classes called behaviors.</span></span> <span data-ttu-id="6264e-192">Zde <xref:System.ServiceModel.ServiceBehaviorAttribute> třída se používá k určení, že je typ služby s více vlákny.</span><span class="sxs-lookup"><span data-stu-id="6264e-192">Here, the <xref:System.ServiceModel.ServiceBehaviorAttribute> class is used to specify that the service type is to be multithreaded.</span></span>  
  
```  
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple]  
public class DerivativesCalculatorServiceType: IDerivativesCalculator  
```  
  
 <span data-ttu-id="6264e-193">Některé chování jako <xref:System.ServiceModel.ServiceBehaviorAttribute>, atributů.</span><span class="sxs-lookup"><span data-stu-id="6264e-193">Some behaviors, like <xref:System.ServiceModel.ServiceBehaviorAttribute>, are attributes.</span></span> <span data-ttu-id="6264e-194">Ostatní těm, které jsou s vlastnostmi, které správce chtít nastavit, můžete změnit v konfiguraci aplikace.</span><span class="sxs-lookup"><span data-stu-id="6264e-194">Others, the ones with properties that administrators would want to set, can be modified in the configuration of an application.</span></span>  
  
 <span data-ttu-id="6264e-195">V programování typů služeb, často využívání <xref:System.ServiceModel.OperationContext> třídy.</span><span class="sxs-lookup"><span data-stu-id="6264e-195">In programming service types, frequent use is made of the <xref:System.ServiceModel.OperationContext> class.</span></span> <span data-ttu-id="6264e-196">Jeho statické <xref:System.ServiceModel.OperationContext.Current%2A> vlastnost poskytuje přístup k informacím o kontextu, ve kterém je spuštěna operace.</span><span class="sxs-lookup"><span data-stu-id="6264e-196">Its static <xref:System.ServiceModel.OperationContext.Current%2A> property provides access to information about the context in which an operation is running.</span></span> <span data-ttu-id="6264e-197"><xref:System.ServiceModel.OperationContext> je podobná i <xref:System.Web.HttpContext> a <xref:System.EnterpriseServices.ContextUtil> třídy.</span><span class="sxs-lookup"><span data-stu-id="6264e-197"><xref:System.ServiceModel.OperationContext> is similar to both the <xref:System.Web.HttpContext> and <xref:System.EnterpriseServices.ContextUtil> classes.</span></span>  
  
## <a name="hosting"></a><span data-ttu-id="6264e-198">Hostování</span><span class="sxs-lookup"><span data-stu-id="6264e-198">Hosting</span></span>  
 <span data-ttu-id="6264e-199">Webových služeb ASP.NET kompilovány do sestavení knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="6264e-199">ASP.NET Web services are compiled into a class library assembly.</span></span> <span data-ttu-id="6264e-200">Soubor s názvem souboru služby je za předpokladu, že má .asmx rozšíření a obsahuje `@ WebService` direktiva, která identifikuje třídu, která obsahuje kód pro tuto službu a sestavení, ve kterém se nachází.</span><span class="sxs-lookup"><span data-stu-id="6264e-200">A file called the service file is provided that has the extension .asmx and contains an `@ WebService` directive that identifies the class that contains the code for the service and the assembly in which it is located.</span></span>  
  
```  
<%@ WebService Language="C#" Class="Service,ServiceAssembly" %>  
```  
  
 <span data-ttu-id="6264e-201">Soubor služby se zkopíruje do kořenový adresář aplikace ASP.NET v Internetové informační služby (IIS) a sestavení se zkopíruje do podadresáři \bin tento kořenový adresář aplikace.</span><span class="sxs-lookup"><span data-stu-id="6264e-201">The service file is copied into an ASP.NET application root in Internet Information Services (IIS), and the assembly is copied into the \bin subdirectory of that application root.</span></span> <span data-ttu-id="6264e-202">Aplikace je pak přístupné pomocí uniform resource locator (URL) souboru služby v kořenovém adresáři aplikace.</span><span class="sxs-lookup"><span data-stu-id="6264e-202">The application is then accessible by using the uniform resource locator (URL) of the service file in the application root.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="6264e-203"> služby se dají snadno hostovat v rámci služby IIS 5.1 nebo 6.0, proces aktivace služby WAS (Windows), je dodáván jako součást služby IIS 7.0, a v rámci všech aplikací .NET.</span><span class="sxs-lookup"><span data-stu-id="6264e-203"> services can readily be hosted within IIS 5.1 or 6.0, the Windows Process Activation Service (WAS) that is provided as part of IIS 7.0, and within any .NET application.</span></span> <span data-ttu-id="6264e-204">K hostování služby IIS 5.1 nebo 6.0, musíte službu používají protokol HTTP jako protokol pro přenos komunikace.</span><span class="sxs-lookup"><span data-stu-id="6264e-204">To host a service in IIS 5.1 or 6.0, the service must use HTTP as the communications transport protocol.</span></span>  
  
 <span data-ttu-id="6264e-205">K hostování služby v rámci služby IIS 5.1, 6.0 nebo WAS, použijte postup následovně:</span><span class="sxs-lookup"><span data-stu-id="6264e-205">To host a service within IIS 5.1, 6.0 or within WAS, use the follows steps:</span></span>  
  
1.  <span data-ttu-id="6264e-206">Zkompilujte typ služby do sestavení knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="6264e-206">Compile the service type into a class library assembly.</span></span>  
  
2.  <span data-ttu-id="6264e-207">Vytvoření služby souboru s příponou .svc s `@ ServiceHost` – direktiva k identifikaci typ služby:</span><span class="sxs-lookup"><span data-stu-id="6264e-207">Create a service file with a .svc extension with an `@ ServiceHost` directive to identify the service type:</span></span>  
  
    ```  
    <%@ServiceHost language="c#" Service="MyService" %>  
    ```  
  
3.  <span data-ttu-id="6264e-208">Zkopírujte soubor služby do virtuálního adresáře a sestavení, v podadresáři \bin tento virtuální adresář.</span><span class="sxs-lookup"><span data-stu-id="6264e-208">Copy the service file into a virtual directory, and the assembly into the \bin subdirectory of that virtual directory.</span></span>  
  
4.  <span data-ttu-id="6264e-209">Zkopírujte konfigurační soubor do virtuálního adresáře a název souboru Web.config.</span><span class="sxs-lookup"><span data-stu-id="6264e-209">Copy the configuration file into the virtual directory, and name it Web.config.</span></span>  
  
 <span data-ttu-id="6264e-210">Aplikace je pak přístupné pomocí adresu URL souboru služby v kořenovém adresáři aplikace.</span><span class="sxs-lookup"><span data-stu-id="6264e-210">The application is then accessible by using the URL of the service file in the application root.</span></span>  
  
 <span data-ttu-id="6264e-211">Na hostitele [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby v rámci aplikace .NET, zkompilovat typ služby do třídy knihovny sestavení odkazuje aplikace a aplikaci na hostitele služby pomocí <xref:System.ServiceModel.ServiceHost> třídy.</span><span class="sxs-lookup"><span data-stu-id="6264e-211">To host a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service within a .NET application, compile the service type into a class library assembly referenced by the application, and program the application to host the service using the <xref:System.ServiceModel.ServiceHost> class.</span></span> <span data-ttu-id="6264e-212">Následuje příklad základní programování vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="6264e-212">The following is an example of the basic programming required:</span></span>  
  
```  
string httpBaseAddress = "http://www.contoso.com:8000/";  
string tcpBaseAddress = "net.tcp://www.contoso.com:8080/";  
  
Uri httpBaseAddressUri = new Uri(httpBaseAddress);  
Uri tcpBaseAddressUri = new Uri(tcpBaseAddress);  
  
Uri[] baseAdresses = new Uri[] {   
 httpBaseAddressUri,  
 tcpBaseAddressUri};  
  
using(ServiceHost host = new ServiceHost(  
typeof(Service), //"Service" is the name of the service type baseAdresses))  
{  
     host.Open();  
  
     […] //Wait to receive messages  
     host.Close();  
}  
```  
  
 <span data-ttu-id="6264e-213">Tento příklad ukazuje, jak jsou při sestavování zadané adresy pro jeden nebo více přenosové protokoly <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="6264e-213">This example shows how addresses for one or more transport protocols are specified in the construction of a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="6264e-214">Tyto adresy jsou označovány jako základní adresy.</span><span class="sxs-lookup"><span data-stu-id="6264e-214">These addresses are referred to as base addresses.</span></span>  
  
 <span data-ttu-id="6264e-215">Adresa zadaná pro libovolný koncový bod služby [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby se jedná o adresu relativně k základní adresa hostitele pro koncový bod.</span><span class="sxs-lookup"><span data-stu-id="6264e-215">The address provided for any endpoint of a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service is an address relative to a base address of the endpoint’s host.</span></span> <span data-ttu-id="6264e-216">Hostitel může mít jeden základní adresa pro každý protokol pro přenos komunikace.</span><span class="sxs-lookup"><span data-stu-id="6264e-216">The host can have one base address for each communication transport protocol.</span></span> <span data-ttu-id="6264e-217">V konfiguraci ukázka v předchozím konfiguračním souboru <xref:System.ServiceModel.BasicHttpBinding> vybrané pro používá koncový bod HTTP jako protokol pro přenos, takže adresa koncového bodu, `EchoService`, je relativní vzhledem k základní adresu HTTP hostitele.</span><span class="sxs-lookup"><span data-stu-id="6264e-217">In the sample configuration in the preceding configuration file, the <xref:System.ServiceModel.BasicHttpBinding> selected for the endpoint uses HTTP as the transport protocol, so the address of the endpoint, `EchoService`, is relative to the host’s HTTP base address.</span></span> <span data-ttu-id="6264e-218">V případě hostitele v předchozím příkladu je základní adresu HTTP http://www.contoso.com:8000/.</span><span class="sxs-lookup"><span data-stu-id="6264e-218">In the case of the host in the preceding example, the HTTP base address is http://www.contoso.com:8000/.</span></span> <span data-ttu-id="6264e-219">Pro služby hostované v rámci služby IIS nebo WAS základní adresa je adresa URL souboru služby, služby.</span><span class="sxs-lookup"><span data-stu-id="6264e-219">For a service hosted within IIS or WAS, the base address is the URL of the service’s service file.</span></span>  
  
 <span data-ttu-id="6264e-220">Pouze služby hostované ve službě IIS nebo WAS a které jsou nakonfigurované s protokolem HTTP jako přenosový protokol výhradně, lze používat [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] možnost režim kompatibility ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="6264e-220">Only services hosted in IIS or WAS, and which are configured with HTTP as the transport protocol exclusively, can be made to use [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ASP.NET compatibility mode option.</span></span> <span data-ttu-id="6264e-221">Tuto možnost zapnete vyžaduje následující kroky.</span><span class="sxs-lookup"><span data-stu-id="6264e-221">Turning that option on requires the following steps.</span></span>  
  
1.  <span data-ttu-id="6264e-222">Musíte přidat programátorů <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> atribut typu služby a určit, že režim kompatibility ASP.NET je buď povoleno nebo požadováno.</span><span class="sxs-lookup"><span data-stu-id="6264e-222">The programmer must add the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> attribute to the service type and specify that ASP.NET compatibility mode is either allowed or required.</span></span>  
  
    ```  
    [System.ServiceModel.Activation.AspNetCompatibilityRequirements(  
          RequirementsMode=AspNetCompatbilityRequirementsMode.Require)]  
    public class DerivativesCalculatorServiceType: IDerivativesCalculator  
    ```  
  
2.  <span data-ttu-id="6264e-223">Správce musí nakonfigurovat aplikaci, aby používala režim kompatibility ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="6264e-223">The administrator must configure the application to use the ASP.NET compatibility mode.</span></span>  
  
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
  
     [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="6264e-224"> aplikace, můžete nakonfigurovat také používat pro své služby souborů a nikoli .svc .asmx jako rozšíření.</span><span class="sxs-lookup"><span data-stu-id="6264e-224"> applications can also be configured to use .asmx as the extension for their service files rather than .svc.</span></span>  
  
    ```xml  
    <system.web>  
         <compilation>  
          <compilation debug="true">  
          <buildProviders>  
           <remove extension=".asmx"/>  
           <add extension=".asmx"   
            type="System.ServiceModel.ServiceBuildProvider,   
            Systemm.ServiceModel,   
            Version=3.0.0.0,   
            Culture=neutral,   
            PublicKeyToken=b77a5c561934e089" />  
          </buildProviders>  
          </compilation>  
         </compilation>  
    </system.web>  
    ```  
  
     <span data-ttu-id="6264e-225">Možnost již nebudete muset změnit klienty, které jsou nakonfigurované na použití adresy URL služby souborů .asmx Pokud chcete použít při úpravě služby [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6264e-225">That option can save you from having to modify clients that are configured to use the URLs of .asmx service files when modifying a service to use [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
## <a name="client-development"></a><span data-ttu-id="6264e-226">Vývoj pro klienta</span><span class="sxs-lookup"><span data-stu-id="6264e-226">Client Development</span></span>  
 <span data-ttu-id="6264e-227">Klienti pro ASP.NET Web services jsou generovány pomocí nástroje příkazového řádku, WSDL.exe, který obsahuje adresu URL souboru .asmx jako vstup.</span><span class="sxs-lookup"><span data-stu-id="6264e-227">Clients for ASP.NET Web services are generated using the command-line tool, WSDL.exe, which provides the URL of the .asmx file as input.</span></span> <span data-ttu-id="6264e-228">Nástroj odpovídající poskytované [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] je [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="6264e-228">The corresponding tool provided by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="6264e-229">Vygeneruje kód modul s definici kontraktu služby a definice [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] třída klienta.</span><span class="sxs-lookup"><span data-stu-id="6264e-229">It generates a code module with the definition of the service contract and the definition of a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client class.</span></span> <span data-ttu-id="6264e-230">Také vytváří konfigurační soubor s adresou a vazby služby.</span><span class="sxs-lookup"><span data-stu-id="6264e-230">It also generates a configuration file with the address and binding of the service.</span></span>  
  
 <span data-ttu-id="6264e-231">V programování klienta vzdálené služby je většinou vhodné programu podle asynchronní vzor.</span><span class="sxs-lookup"><span data-stu-id="6264e-231">In programming a client of a remote service it is generally advisable to program according to an asynchronous pattern.</span></span> <span data-ttu-id="6264e-232">Kód vygenerovaný nástroj WSDL.exe vždy poskytuje pro synchronní a asynchronní vzor ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="6264e-232">The code generated by the WSDL.exe tool always provides for both a synchronous and an asynchronous pattern by default.</span></span> <span data-ttu-id="6264e-233">Kód vygenerovaný [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) můžete zadat buď vzor.</span><span class="sxs-lookup"><span data-stu-id="6264e-233">The code generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) can provide for either pattern.</span></span> <span data-ttu-id="6264e-234">Poskytuje synchronní vzor ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="6264e-234">It provides for the synchronous pattern by default.</span></span> <span data-ttu-id="6264e-235">Pokud je nástroj spuštěn s `/async` přepínače, pak poskytuje generovaný kód pro asynchronní vzor.</span><span class="sxs-lookup"><span data-stu-id="6264e-235">If the tool is executed with the `/async` switch, then the generated code provides for the asynchronous pattern.</span></span>  
  
 <span data-ttu-id="6264e-236">Není zaručeno, že názvy v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ASP vygenerované třídy klienta. Nástroj WSDL.exe NET je ve výchozím nastavení, odpovídat názvům v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nástroje Svcutil.exe vygenerované třídy klienta.</span><span class="sxs-lookup"><span data-stu-id="6264e-236">There is no guarantee that names in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client classes generated by ASP.NET’s WSDL.exe tool, by default, match the names in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client classes generated by the Svcutil.exe tool.</span></span> <span data-ttu-id="6264e-237">Na konkrétní názvy vlastnosti tříd, které mají k serializaci pomocí <xref:System.Xml.Serialization.XmlSerializer> ve výchozím nastavení, mají v kód vygenerovaný nástroje Svcutil.exe, která není v případě s nástroj WSDL.exe příponu vlastnost.</span><span class="sxs-lookup"><span data-stu-id="6264e-237">In particular, the names of the properties of classes that have to be serialized using the <xref:System.Xml.Serialization.XmlSerializer> are, by default, given the suffix Property in the code generated by the Svcutil.exe tool, which is not the case with the WSDL.exe tool.</span></span>  
  
## <a name="message-representation"></a><span data-ttu-id="6264e-238">Reprezentace zprávy</span><span class="sxs-lookup"><span data-stu-id="6264e-238">Message Representation</span></span>  
 <span data-ttu-id="6264e-239">Hlavičky SOAP zpráv odesílaných i přijímaných v: webových služeb ASP.NET můžete přizpůsobit.</span><span class="sxs-lookup"><span data-stu-id="6264e-239">The headers of the SOAP messages sent and received by ASP.NET Web services can be customized.</span></span> <span data-ttu-id="6264e-240">Třída je odvozený od <xref:System.Web.Services.Protocols.SoapHeader> definovat strukturu hlavičky a potom <xref:System.Web.Services.Protocols.SoapHeaderAttribute> slouží k určení přítomnosti záhlaví.</span><span class="sxs-lookup"><span data-stu-id="6264e-240">A class is derived from <xref:System.Web.Services.Protocols.SoapHeader> to define the structure of the header, and then the <xref:System.Web.Services.Protocols.SoapHeaderAttribute> is used to indicate the presence of the header.</span></span>  
  
```  
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
  
 <span data-ttu-id="6264e-241">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Poskytuje atributy, <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute>, a <xref:System.ServiceModel.MessageBodyMemberAttribute> k popisu struktury protokolu SOAP zprávy odeslané a přijaté službou.</span><span class="sxs-lookup"><span data-stu-id="6264e-241">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provides the attributes, <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute>, and <xref:System.ServiceModel.MessageBodyMemberAttribute> to describe the structure of the SOAP messages sent and received by a service.</span></span>  
  
```  
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
public class ItemMesage  
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
  
 <span data-ttu-id="6264e-242">Tuto syntaxi vypočítá explicitní reprezentace strukturu zprávy, zatímco strukturu zprávy je zahrnuto v kódu webové služby technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="6264e-242">This syntax yields an explicit representation of the structure of the messages, whereas the structure of messages is implied by the code of an ASP.NET Web service.</span></span> <span data-ttu-id="6264e-243">Také v syntaxi ASP.NET hlavičky zpráv jsou reprezentovány jako vlastnosti služby, například `ProtocolHeader` vlastnost v předchozím příkladu, zatímco v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] syntaxi, která jsou přesněji reprezentována jako vlastnosti zprávy.</span><span class="sxs-lookup"><span data-stu-id="6264e-243">Also, in the ASP.NET syntax, message headers are represented as properties of the service, such as the `ProtocolHeader` property in the previous example, whereas in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] syntax, they are more accurately represented as properties of messages.</span></span> <span data-ttu-id="6264e-244">Navíc [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] umožňuje hlavičky zpráv, který se má přidat ke konfiguraci koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="6264e-244">Also, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] allows message headers to be added to the configuration of endpoints.</span></span>  
  
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
  
 <span data-ttu-id="6264e-245">Možnost umožňuje vyhnout se všechny odkazy na infrastruktury protokolu hlavičky v kódu pro klienta služby nebo: hlavičky jsou přidány do zprávy z důvodu konfigurace koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="6264e-245">That option allows you to avoid any reference to infrastructural protocol headers in the code for a client or service: the headers are added to messages because of how the endpoint is configured.</span></span>  
  
## <a name="service-description"></a><span data-ttu-id="6264e-246">Popis služby</span><span class="sxs-lookup"><span data-stu-id="6264e-246">Service Description</span></span>  
 <span data-ttu-id="6264e-247">Vydání požadavku HTTP GET pro soubor .asmx ASP.NET webové služby s dotazem WSDL způsobí, že ASP.NET, aby generoval WSDL k popisu služby.</span><span class="sxs-lookup"><span data-stu-id="6264e-247">Issuing an HTTP GET request for the .asmx file of an ASP.NET Web service with the query WSDL causes ASP.NET to generate WSDL to describe the service.</span></span> <span data-ttu-id="6264e-248">Vrací, které WSDL jako odpověď na žádost.</span><span class="sxs-lookup"><span data-stu-id="6264e-248">It returns that WSDL as the response to the request.</span></span>  
  
 <span data-ttu-id="6264e-249">ASP.NET 2.0 možné ověřit, jestli je kompatibilní s Basic Profile 1.1 organizace interoperabilita služby webové služby (WS-I) a vložit deklaraci, zda je služba kompatibilní do své WSDL.</span><span class="sxs-lookup"><span data-stu-id="6264e-249">ASP.NET 2.0 made it possible to validate that a service is compliant with the Basic Profile 1.1 of the Web Services-Interoperability Organization (WS-I), and to insert a claim that the service is compliant into its WSDL.</span></span> <span data-ttu-id="6264e-250">To znamená done pomocí `ConformsTo` a `EmitConformanceClaims` parametry <xref:System.Web.Services.WebServiceBindingAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="6264e-250">That is done using the `ConformsTo` and `EmitConformanceClaims` parameters of the <xref:System.Web.Services.WebServiceBindingAttribute> attribute.</span></span>  
  
```  
[WebService(Namespace = "http://tempuri.org/")]  
[WebServiceBinding(  
     ConformsTo = WsiProfiles.BasicProfile1_1,  
     EmitConformanceClaims=true)]  
public interface IEcho  
```  
  
 <span data-ttu-id="6264e-251">WSDL, který ASP.NET generuje pro službu lze přizpůsobit.</span><span class="sxs-lookup"><span data-stu-id="6264e-251">The WSDL that ASP.NET generates for a service can be customized.</span></span> <span data-ttu-id="6264e-252">Přizpůsobení probíhají vytvořením třídy odvozené z <xref:System.Web.Services.Description.ServiceDescriptionFormatExtension> k přidávání položek do schématu WSDL.</span><span class="sxs-lookup"><span data-stu-id="6264e-252">Customizations are made by creating a derived class of <xref:System.Web.Services.Description.ServiceDescriptionFormatExtension> to add items to the WSDL.</span></span>  
  
 <span data-ttu-id="6264e-253">Vydání požadavku HTTP GET s dotazem WSDL pro soubor .svc z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby s hostovaným v rámci služby IIS 51, 6.0 nebo WAS příčiny koncový bod HTTP [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] reagovat s WSDL k popisu služby.</span><span class="sxs-lookup"><span data-stu-id="6264e-253">Issuing an HTTP GET request with the query WSDL for the .svc file of a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service with an HTTP endpoint hosted within IIS 51, 6.0 or WAS causes [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] to respond with WSDL to describe the service.</span></span> <span data-ttu-id="6264e-254">Vydání požadavku HTTP GET s dotazem WSDL základní adresu HTTP služby hostované v rámci aplikace .NET má stejný účinek, pokud httpGetEnabled nastavena na hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="6264e-254">Issuing an HTTP GET request with the query WSDL to the HTTP base address of a service hosted within a .NET application has the same effect if httpGetEnabled is set to true.</span></span>  
  
 <span data-ttu-id="6264e-255">Ale [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] také odpovídá na požadavky služby WS-MetadataExchange s WSDL, který ho generuje k popisu služby.</span><span class="sxs-lookup"><span data-stu-id="6264e-255">However, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] also responds to WS-MetadataExchange requests with WSDL that it generates to describe a service.</span></span> <span data-ttu-id="6264e-256">Webových služeb ASP.NET nemají integrovanou podporu pro WS-MetadataExchange požadavky.</span><span class="sxs-lookup"><span data-stu-id="6264e-256">ASP.NET Web services do not have built-in support for WS-MetadataExchange requests.</span></span>  
  
 <span data-ttu-id="6264e-257">Schématu WSDL který [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generuje lze hojně přizpůsobit.</span><span class="sxs-lookup"><span data-stu-id="6264e-257">The WSDL that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates can be extensively customized.</span></span> <span data-ttu-id="6264e-258"><xref:System.ServiceModel.Description.ServiceMetadataBehavior> Třída zajišťuje některé funkce pro přizpůsobení schématu WSDL.</span><span class="sxs-lookup"><span data-stu-id="6264e-258">The <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class provides some facilities for customizing the WSDL.</span></span> <span data-ttu-id="6264e-259">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Je také možné nakonfigurovat negeneruje WSDL, ale spíše na použití statických souborů WSDL na dané adrese URL.</span><span class="sxs-lookup"><span data-stu-id="6264e-259">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] can also be configured to not generate WSDL, but rather to use a static WSDL file at a given URL.</span></span>  
  
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
  
## <a name="exception-handling"></a><span data-ttu-id="6264e-260">Zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="6264e-260">Exception Handling</span></span>  
 <span data-ttu-id="6264e-261">Nezpracované výjimky jsou v webových služeb ASP.NET, vracené klientům. jako chyb SOAP.</span><span class="sxs-lookup"><span data-stu-id="6264e-261">In ASP.NET Web services, unhandled exceptions are returned to clients as SOAP faults.</span></span> <span data-ttu-id="6264e-262">Můžete také explicitně vyvolat instance <xref:System.Web.Services.Protocols.SoapException> třídy a mít větší kontrolu nad obsah chybu protokolu SOAP, který získá odeslány klientovi.</span><span class="sxs-lookup"><span data-stu-id="6264e-262">You can also explicitly throw instances of the <xref:System.Web.Services.Protocols.SoapException> class and have more control over the content of the SOAP fault that gets transmitted to the client.</span></span>  
  
 <span data-ttu-id="6264e-263">V [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby, neošetřených výjimek nebudou zobrazeny na klienty jako chyb SOAP, aby se zabránilo citlivé informace, které můžou neúmyslně zpřístupnit prostřednictvím výjimky.</span><span class="sxs-lookup"><span data-stu-id="6264e-263">In [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services, unhandled exceptions are not returned to clients as SOAP faults to prevent sensitive information being inadvertently exposed through the exceptions.</span></span> <span data-ttu-id="6264e-264">Nastavení konfigurace je k dispozici do mají neošetřené výjimky vracené klientům. pro účely ladění.</span><span class="sxs-lookup"><span data-stu-id="6264e-264">A configuration setting is provided to have unhandled exceptions returned to clients for the purpose of debugging.</span></span>  
  
 <span data-ttu-id="6264e-265">Pokud chcete vrátit chyb SOAP klientům, můžete vyvolat instancí obecného typu <xref:System.ServiceModel.FaultException%601>pomocí kontraktu dat typu jako obecného typu.</span><span class="sxs-lookup"><span data-stu-id="6264e-265">To return SOAP faults to clients, you can throw instances of the generic type, <xref:System.ServiceModel.FaultException%601>, using the data contract type as the generic type.</span></span> <span data-ttu-id="6264e-266">Můžete také přidat <xref:System.ServiceModel.FaultContractAttribute> atributů k operacím k určení chyb, které může yield operace.</span><span class="sxs-lookup"><span data-stu-id="6264e-266">You can also add <xref:System.ServiceModel.FaultContractAttribute> attributes to operations to specify the faults that an operation might yield.</span></span>  
  
```  
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
  
 <span data-ttu-id="6264e-267">To tak, že má za následek možné chyby inzerovaných ve schématu WSDL pro službu, umožňuje tak klientským programátorům předvídat chyb, které můžete výsledkem operace a zápisu že odpovídající catch příkazy.</span><span class="sxs-lookup"><span data-stu-id="6264e-267">Doing so results in the possible faults being advertised in the WSDL for the service, allowing client programmers to anticipate which faults can result from an operation, and write the appropriate catch statements.</span></span>  
  
```  
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
  
## <a name="state-management"></a><span data-ttu-id="6264e-268">Stav správy</span><span class="sxs-lookup"><span data-stu-id="6264e-268">State Management</span></span>  
 <span data-ttu-id="6264e-269">Třída, která slouží k implementaci ASP.NET webové služby může být odvozen od <xref:System.Web.Services.WebService>.</span><span class="sxs-lookup"><span data-stu-id="6264e-269">The class used to implement an ASP.NET Web service may be derived from <xref:System.Web.Services.WebService>.</span></span>  
  
```  
public class Service : WebService, IEcho  
{  
  
 public string Echo(string input)  
 {  
  return input;  
 }  
}  
```  
  
 <span data-ttu-id="6264e-270">V takovém případě třída může být naprogramovaný tak, aby použít <xref:System.Web.Services.WebService> základní kontext vlastnosti třídy se pro přístup k <xref:System.Web.HttpContext> objektu.</span><span class="sxs-lookup"><span data-stu-id="6264e-270">In that case, the class can be programmed to use the <xref:System.Web.Services.WebService> base class’ Context property to access a <xref:System.Web.HttpContext> object.</span></span> <span data-ttu-id="6264e-271"><xref:System.Web.HttpContext> Objekt lze použít k aktualizaci a načíst informace o stavu aplikace pomocí jeho vlastnosti aplikace a slouží k aktualizaci a načíst informace o stavu relace pomocí jeho vlastnost relace.</span><span class="sxs-lookup"><span data-stu-id="6264e-271">The <xref:System.Web.HttpContext> object can be used to update and retrieve application state information by using its Application property, and can be used to update and retrieve session state information by using its Session property.</span></span>  
  
 <span data-ttu-id="6264e-272">Technologie ASP.NET poskytuje značnou kontrolu nad kde stavu relace informace přistupovat pomocí vlastnosti relace <xref:System.Web.HttpContext> je ve skutečnosti uložen.</span><span class="sxs-lookup"><span data-stu-id="6264e-272">ASP.NET provides considerable control over where the session state information accessed by using the Session property of the <xref:System.Web.HttpContext> is actually stored.</span></span> <span data-ttu-id="6264e-273">Může být uložená v souborech cookie, v databázi, v paměti aktuálního serveru nebo v paměti na určený server.</span><span class="sxs-lookup"><span data-stu-id="6264e-273">It may be stored in cookies, in a database, in the memory of the current server, or in the memory of a designated server.</span></span> <span data-ttu-id="6264e-274">Volba se provádí v konfiguračním souboru služby.</span><span class="sxs-lookup"><span data-stu-id="6264e-274">The choice is made in the service’s configuration file.</span></span>  
  
 <span data-ttu-id="6264e-275">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Poskytuje rozšiřitelné objekty pro správu stavu.</span><span class="sxs-lookup"><span data-stu-id="6264e-275">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provides extensible objects for state management.</span></span> <span data-ttu-id="6264e-276">Rozšiřitelné objekty jsou objekty, které implementují <xref:System.ServiceModel.IExtensibleObject%601>.</span><span class="sxs-lookup"><span data-stu-id="6264e-276">Extensible objects are objects that implement <xref:System.ServiceModel.IExtensibleObject%601>.</span></span> <span data-ttu-id="6264e-277">Nejdůležitější rozšiřitelné objekty jsou <xref:System.ServiceModel.ServiceHostBase> a <xref:System.ServiceModel.InstanceContext>.</span><span class="sxs-lookup"><span data-stu-id="6264e-277">The most important extensible objects are <xref:System.ServiceModel.ServiceHostBase> and <xref:System.ServiceModel.InstanceContext>.</span></span> <span data-ttu-id="6264e-278">`ServiceHostBase` umožňuje udržovat stav všech instancí služby všechny typy na stejném hostiteli mohou získat přístup, při `InstanceContext` umožňuje udržovat stav, který je přístupný pomocí žádný kód běžící v rámci stejné instance typu služby.</span><span class="sxs-lookup"><span data-stu-id="6264e-278">`ServiceHostBase` allows you to maintain state that all of the instances of all of the service types on the same host can access, while `InstanceContext` allows you to maintain state that can be accessed by any code running within the same instance of a service type.</span></span>  
  
 <span data-ttu-id="6264e-279">Tady, typ služby `TradingSystem`, má <xref:System.ServiceModel.ServiceBehaviorAttribute> který určuje, že všechna volání ze stejné [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] instanci klienta jsou směrovány na stejnou instanci typu služby.</span><span class="sxs-lookup"><span data-stu-id="6264e-279">Here, the service type, `TradingSystem`, has a <xref:System.ServiceModel.ServiceBehaviorAttribute> that specifies that all calls from the same [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client instance are routed to the same instance of the service type.</span></span>  
  
```  
[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerSession)]  
public class TradingSystem: ITradingService  
```  
  
 <span data-ttu-id="6264e-280">Třída, `DealData`, definuje stav, který je přístupný pomocí jakékoli kód spuštěný ve stejné instanci typu služby.</span><span class="sxs-lookup"><span data-stu-id="6264e-280">The class, `DealData`, defines state that can be accessed by any code running in the same instance of a service type.</span></span>  
  
```  
internal class DealData: IExtension<InstanceContext>  
{  
 public string DealIdentifier = null;  
 public Trade[] Trades = null;  
}  
```  
  
 <span data-ttu-id="6264e-281">V kódu typu služby, který implementuje některé z operací kontrakt služby `DealData` stav objektu se přidá do stavu aktuální instance typu služby.</span><span class="sxs-lookup"><span data-stu-id="6264e-281">In the code of the service type that implements one of the operations of the service contract, a `DealData` state object is added to the state of the current instance of the service type.</span></span>  
  
```  
string ITradingService.BeginDeal()  
{  
 string dealIdentifier = Guid.NewGuid().ToString();  
 DealData state = new DealData(dealIdentifier);  
 OperationContext.Current.InstanceContext.Extensions.Add(state);  
 return dealIdentifier;  
}  
```  
  
 <span data-ttu-id="6264e-282">Tento objekt stavu můžete pak načíst a upravovat kód, který implementuje jiné operace kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="6264e-282">That state object can then be retrieved and modified by the code that implements another of the service contract’s operations.</span></span>  
  
```  
void ITradingService.AddTrade(Trade trade)  
{  
 DealData dealData =  OperationContext.Current.InstanceContext.Extensions.Find<DealData>();  
 dealData.AddTrade(trade);  
}  
```  
  
 <span data-ttu-id="6264e-283">Zatímco technologie ASP.NET poskytuje ovládací prvek přes kde stavu informace v <xref:System.Web.HttpContext> třída je ve skutečnosti uložena, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], alespoň v jeho počáteční verze poskytuje žádnou kontrolu nad úložiště rozšiřitelné objekty.</span><span class="sxs-lookup"><span data-stu-id="6264e-283">Whereas ASP.NET provides control over where state information in the <xref:System.Web.HttpContext> class is actually stored, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], at least in its initial version, provides no control over where extensible objects are stored.</span></span> <span data-ttu-id="6264e-284">Která se považuje za velmi nejlepší důvod pro režim kompatibility ASP.NET pro výběr [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby.</span><span class="sxs-lookup"><span data-stu-id="6264e-284">That constitutes the very best reason for selecting the ASP.NET compatibility mode for a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="6264e-285">Pokud je nutné konfigurovat stav správy, pak pro režim kompatibility ASP.NET výslovném umožňuje používat zařízení <xref:System.Web.HttpContext> třída přesně tak, jak se používají v technologii ASP.NET a taky nakonfigurovat kde stavu informace, které jsou spravované pomocí <xref:System.Web.HttpContext> třída je uložena.</span><span class="sxs-lookup"><span data-stu-id="6264e-285">If configurable state management is imperative, then opting for the ASP.NET compatibility mode allows you to use the facilities of the <xref:System.Web.HttpContext> class exactly as they are used in ASP.NET, and also to configure where state information managed by using the <xref:System.Web.HttpContext> class is stored.</span></span>  
  
## <a name="security"></a><span data-ttu-id="6264e-286">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="6264e-286">Security</span></span>  
 <span data-ttu-id="6264e-287">Možnosti zabezpečení rozhraní ASP.NET Web služeb jsou pro zabezpečení všechny aplikace služby IIS.</span><span class="sxs-lookup"><span data-stu-id="6264e-287">The options for securing ASP.NET Web services are those for securing any IIS application.</span></span> <span data-ttu-id="6264e-288">Protože [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace může být hostovaný nejen v rámci služby IIS, ale i v rámci všech spustitelný soubor, .NET možnosti zabezpečení [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace musí být provedeny nezávislá funkce služby IIS.</span><span class="sxs-lookup"><span data-stu-id="6264e-288">Because [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications can be hosted not only within IIS but also within any .NET executable, the options for securing [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications must be made independent from the facilities of IIS.</span></span> <span data-ttu-id="6264e-289">Zařízení, které jsou pro ASP.NET Web services jsou však také k dispozici pro [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby spuštěné v režimu kompatibility ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="6264e-289">However, the facilities provided for ASP.NET Web services are also available for [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services running in ASP.NET compatibility mode.</span></span>  
  
### <a name="security-authentication"></a><span data-ttu-id="6264e-290">Zabezpečení: ověřování</span><span class="sxs-lookup"><span data-stu-id="6264e-290">Security: Authentication</span></span>  
 <span data-ttu-id="6264e-291">Služba IIS poskytuje možnosti pro řízení přístupu k aplikacím, které můžete vybrat buď anonymní přístup, nebo různé režimy ověřování: ověřování systému Windows, ověřování hodnotou hash, základní ověřování a ověřování .NET Passport.</span><span class="sxs-lookup"><span data-stu-id="6264e-291">IIS provides facilities for controlling access to applications by which you can select either anonymous access or a variety of modes of authentication: Windows Authentication, Digest Authentication, Basic Authentication, and .NET Passport Authentication.</span></span> <span data-ttu-id="6264e-292">Možnost ověřování systému Windows lze použít k řízení přístupu k webové služby ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="6264e-292">The Windows Authentication option can be used to control access to ASP.NET Web services.</span></span> <span data-ttu-id="6264e-293">Ale když [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jsou hostované aplikací v rámci služby IIS, musíte službu IIS konfigurovat tak, aby povolovala anonymní přístup k aplikaci, tak, že ověřování je možné spravovat pomocí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] samostatně, který podporuje ověřování systému Windows mezi různé další Možnosti.</span><span class="sxs-lookup"><span data-stu-id="6264e-293">However, when [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications are hosted within IIS, IIS must be configured to permit anonymous access to the application, so that authentication can be managed by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] itself, which does support Windows authentication among various other options.</span></span> <span data-ttu-id="6264e-294">Další možnosti, které jsou integrované zahrnovat uživatelské jméno tokeny, certifikáty X.509, tokeny SAML a služba CardSpace karet, ale může být také definováno vlastních ověřovacích mechanismů.</span><span class="sxs-lookup"><span data-stu-id="6264e-294">The other options that are built-in include username tokens, X.509 certificates, SAML tokens, and CardSpace card, but custom authentication mechanisms can also be defined.</span></span>  
  
### <a name="security-impersonation"></a><span data-ttu-id="6264e-295">Zabezpečení: zosobnění</span><span class="sxs-lookup"><span data-stu-id="6264e-295">Security: Impersonation</span></span>  
 <span data-ttu-id="6264e-296">Technologie ASP.NET poskytuje identity element který ASP.NET webové služby, můžete provést zosobnění konkrétní uživatele nebo přihlašovacích údajů uživatele podle toho, která jsou k dispozici s aktuální požadavek.</span><span class="sxs-lookup"><span data-stu-id="6264e-296">ASP.NET provides an identity element by which an ASP.NET Web service can be made to impersonate a particular user or whichever user’s credentials are provided with the current request.</span></span> <span data-ttu-id="6264e-297">Tento element můžete použít ke konfiguraci zosobnění v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikací, které běží v režimu kompatibility ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="6264e-297">That element can be used to configure impersonation in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications running in ASP.NET compatibility mode.</span></span>  
  
 <span data-ttu-id="6264e-298">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Konfigurační systém poskytuje vlastní element identity pro určení konkrétního uživatele k zosobnění.</span><span class="sxs-lookup"><span data-stu-id="6264e-298">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] configuration system provides its own identity element for designating a particular user to impersonate.</span></span> <span data-ttu-id="6264e-299">Navíc [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby a klienti mohou být nezávisle nakonfigurovaný pro zosobnění.</span><span class="sxs-lookup"><span data-stu-id="6264e-299">Also, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clients and services can be independently configured for impersonation.</span></span> <span data-ttu-id="6264e-300">Klienti lze nakonfigurovat k zosobnění s aktuálním uživatelem při odesílají žádosti.</span><span class="sxs-lookup"><span data-stu-id="6264e-300">Clients can be configured to impersonate the current user when they transmit requests.</span></span>  
  
```xml  
<behaviors>  
     <behavior name="DerivativesCalculatorClientBehavior">  
      <clientCredentials>  
      <windows allowedImpersonationLevel="Impersonation"/>  
      </clientCredentials>  
     </behavior>  
</behaviors>  
```  
  
 <span data-ttu-id="6264e-301">Operace služby se dá nakonfigurovat k zosobnění přihlašovacích údajů uživatele podle toho, která jsou k dispozici s aktuální požadavek.</span><span class="sxs-lookup"><span data-stu-id="6264e-301">Service operations can be configured to impersonate whichever user’s credentials are provided with the current request.</span></span>  
  
```  
[OperationBehavior(Impersonation = ImpersonationOption.Required)]  
public void Receive(Message input)  
```  
  
### <a name="security-authorization-using-access-control-lists"></a><span data-ttu-id="6264e-302">Zabezpečení: Autorizace pomocí seznamů řízení přístupu</span><span class="sxs-lookup"><span data-stu-id="6264e-302">Security: Authorization using Access Control Lists</span></span>  
 <span data-ttu-id="6264e-303">Seznamy řízení přístupu (ACL) umožňuje omezit přístup k souborům .asmx.</span><span class="sxs-lookup"><span data-stu-id="6264e-303">Access Control Lists (ACLs) can be used to restrict access to .asmx files.</span></span> <span data-ttu-id="6264e-304">Nicméně seznamy ACL v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] souborů .svc ignorují kromě v režimu kompatibility ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="6264e-304">However, ACLs on [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] .svc files are ignored except in ASP.NET compatibility mode.</span></span>  
  
### <a name="security-role-based-authorization"></a><span data-ttu-id="6264e-305">Zabezpečení: Ověření na základě Role</span><span class="sxs-lookup"><span data-stu-id="6264e-305">Security: Role-based Authorization</span></span>  
 <span data-ttu-id="6264e-306">Možnost ověřování systému Windows služby IIS lze použít ve spojení s zadaný element autorizace podle jazyka konfigurace ASP.NET pro usnadnění autorizace na základě rolí pro webové služby ASP.NET podle skupiny systému Windows, k nimž uživatelé přiřazeni .</span><span class="sxs-lookup"><span data-stu-id="6264e-306">The IIS Windows Authentication option can be used in conjunction with the authorization element provided by the ASP.NET configuration language to facilitate role-based authorization for ASP.NET Web services based on the Windows groups to which users are assigned.</span></span> <span data-ttu-id="6264e-307">ASP.NET 2.0 zavedená obecnější mechanismus ověřování na základě rolí: zprostředkovatelů rolí.</span><span class="sxs-lookup"><span data-stu-id="6264e-307">ASP.NET 2.0 introduced a more general role-based authorization mechanism: role providers.</span></span>  
  
 <span data-ttu-id="6264e-308">Zprostředkovatelé role jsou třídy, že všechny implementovat základní rozhraní pro dotazující o rolích, ke kterým je přiřazen uživatele, ale každý zprostředkovatele rolí umí k načtení těchto informací z jiného zdroje.</span><span class="sxs-lookup"><span data-stu-id="6264e-308">Role providers are classes that all implement a basic interface for enquiring about the roles to which a user is assigned, but each role provider knows how to retrieve that information from a different source.</span></span> <span data-ttu-id="6264e-309">ASP.NET 2.0 obsahuje role zprostředkovatele, který přiřazení rolí můžete načíst z databáze Microsoft SQL Server a další, které mohou načítat přiřazení rolí ze Správce autorizací systému Windows Server 2003.</span><span class="sxs-lookup"><span data-stu-id="6264e-309">ASP.NET 2.0 provides a role provider that can retrieve role assignments from a Microsoft SQL Server database, and another that can retrieve role assignments from the Windows Server 2003 Authorization Manager.</span></span>  
  
 <span data-ttu-id="6264e-310">Mechanismus poskytovatele role lze použít ve skutečnosti nezávisle na ASP.NET v jakékoli aplikaci .NET, včetně [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="6264e-310">The role provider mechanism can actually be used independently of ASP.NET in any .NET application, including a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application.</span></span> <span data-ttu-id="6264e-311">Následující ukázka konfigurace [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace ukazuje způsob použití poskytovatele rolí prostředí ASP.NET je možnost vybraná prostřednictvím <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.</span><span class="sxs-lookup"><span data-stu-id="6264e-311">The following sample configuration for a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application shows how the use of an ASP.NET role provider is an option selected by means of the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.</span></span>  
  
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
  
### <a name="security-claims-based-authorization"></a><span data-ttu-id="6264e-312">Zabezpečení: Autorizace založené na deklaracích identity</span><span class="sxs-lookup"><span data-stu-id="6264e-312">Security: Claims-based Authorization</span></span>  
 <span data-ttu-id="6264e-313">Jedním z nejdůležitějších inovace z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] je důkladné podpora pro autorizaci přístupu k chráněným prostředkům na základě deklarací.</span><span class="sxs-lookup"><span data-stu-id="6264e-313">One of the most important innovations of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is its thorough support for authorizing access to protected resources based on claims.</span></span> <span data-ttu-id="6264e-314">Deklarace identity skládá z typu, doprava a hodnotu, licence ovladače, třeba.</span><span class="sxs-lookup"><span data-stu-id="6264e-314">Claims consist of a type, a right and a value, a drivers’ license, for example.</span></span> <span data-ttu-id="6264e-315">Umožňuje sadu deklarací identity o nosiče, z nichž jeden je držitele datum narození.</span><span class="sxs-lookup"><span data-stu-id="6264e-315">It makes a set of claims about the bearer, one of which is the bearer’s date of birth.</span></span> <span data-ttu-id="6264e-316">Typ této deklarace identity je datum narození, když hodnota deklarace identity je datum narození ovladače.</span><span class="sxs-lookup"><span data-stu-id="6264e-316">The type of that claim is date of birth, while the value of the claim is the driver’s birth date.</span></span> <span data-ttu-id="6264e-317">Oprávnění, který deklaraci identity svěřuje nosiče Určuje, co dělat s hodnotou deklarace identity nosiče.</span><span class="sxs-lookup"><span data-stu-id="6264e-317">The right that a claim confers on the bearer specifies what the bearer can do with the claim’s value.</span></span> <span data-ttu-id="6264e-318">V případě deklarace identity ovladač datum narození, vpravo se u sebe: ovladač má, datum narození ale nejde, třeba, změnu.</span><span class="sxs-lookup"><span data-stu-id="6264e-318">In the case of the claim of the driver’s date of birth, the right is possession: the driver possesses that date of birth but cannot, for example, alter it.</span></span> <span data-ttu-id="6264e-319">Na základě deklarace autorizace uzavře autorizace na základě rolí, protože role jsou typu deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="6264e-319">Claims-based authorization encloses role-based authorization, because roles are a type of claim.</span></span>  
  
 <span data-ttu-id="6264e-320">Na základě deklarací autorizace provádí porovnávání sadu deklarací identity pro požadavky na přístup operace a to v závislosti na výsledku této porovnání, přidělování nebo odmítání přístupu pro operaci.</span><span class="sxs-lookup"><span data-stu-id="6264e-320">Authorization based on claims is accomplished by comparing a set of claims to the access requirements of the operation and, depending on the outcome of that comparison, granting or denying access to the operation.</span></span> <span data-ttu-id="6264e-321">V [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], můžete zadat třídu se použije ke spuštění na základě deklarace autorizace znovu přiřazením hodnoty na `ServiceAuthorizationManager` vlastnost <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.</span><span class="sxs-lookup"><span data-stu-id="6264e-321">In [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], you can specify a class to use to run claims-based authorization, once again by assigning a value to the `ServiceAuthorizationManager` property of <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.</span></span>  
  
```xml  
<behaviors>  
     <behavior name='ServiceBehavior'>  
     <serviceAuthorization   
     serviceAuthorizationManagerType=  
                   'Service.AccessChecker, Service' />  
     </behavior>  
</behaviors>  
```  
  
 <span data-ttu-id="6264e-322">Třídy používané ke spuštění ověření na základě deklarace identity musí být odvozeny od <xref:System.ServiceModel.ServiceAuthorizationManager>, který má jenom jednu metodu přepsat, `AccessCheck()`.</span><span class="sxs-lookup"><span data-stu-id="6264e-322">Classes used to run claims-based authorization must derive from <xref:System.ServiceModel.ServiceAuthorizationManager>, which has just one method to override, `AccessCheck()`.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="6264e-323"> vždy, když je volána operace služby a poskytuje volá tuto metodu <xref:System.ServiceModel.OperationContext> objekt, který se má deklarace pro uživatele v jeho `ServiceSecurityContext.AuthorizationContext` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="6264e-323"> calls that method whenever an operation of the service is invoked and provides a <xref:System.ServiceModel.OperationContext> object, which has the claims for the user in its `ServiceSecurityContext.AuthorizationContext` property.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="6264e-324"> podporuje práci při sestavování deklarace identity o uživateli z tokenu jakoukoli zabezpečení uživatele zadaná pro ověřování, což ponechá úkolu vyhodnocení, zda tyto deklarace identity stačit pro operace.</span><span class="sxs-lookup"><span data-stu-id="6264e-324"> does the work of assembling claims about the user from whatever security token the user provided for authentication, which leaves the of task of evaluating whether those claims suffice for the operation in question.</span></span>  
  
 <span data-ttu-id="6264e-325">Aby [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] automaticky sestaví deklarace identity z jakéhokoli druhu zabezpečení token je vysoce významnou inovaci, protože je kód pro ověřování založené na deklaracích ke zcela nezávislé na ověřovací mechanismus.</span><span class="sxs-lookup"><span data-stu-id="6264e-325">That [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] automatically assembles claims from any kind of security token is a highly significant innovation, because it makes the code for authorization based on the claims entirely independent of the authentication mechanism.</span></span> <span data-ttu-id="6264e-326">Naopak autorizace pomocí seznamů řízení přístupu nebo role v ASP.NET úzce souvisí ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="6264e-326">By contrast, authorization using ACLs or roles in ASP.NET is closely tied to Windows authentication.</span></span>  
  
### <a name="security-confidentiality"></a><span data-ttu-id="6264e-327">Zabezpečení: důvěrnost</span><span class="sxs-lookup"><span data-stu-id="6264e-327">Security: Confidentiality</span></span>  
 <span data-ttu-id="6264e-328">Důvěrnost zprávy vyměňují s webovými službami ASP.NET můžete zajistit na úrovni přenosu konfigurace aplikace v rámci služby IIS pro používání zabezpečené protokol HTTPS (Hypertext Transfer).</span><span class="sxs-lookup"><span data-stu-id="6264e-328">The confidentiality of messages exchanged with ASP.NET Web services can be ensured at the transport level by configuring the application within IIS to use the Secure Hypertext Transfer Protocol (HTTPS).</span></span> <span data-ttu-id="6264e-329">Totéž můžete provést [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace hostované v rámci služby IIS.</span><span class="sxs-lookup"><span data-stu-id="6264e-329">The same can be done for [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications hosted within IIS.</span></span> <span data-ttu-id="6264e-330">Ale [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace hostované mimo služby IIS lze také nakonfigurovat pro použití protokolu zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="6264e-330">However, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications hosted outside of IIS can also be configured to use a secure transport protocol.</span></span> <span data-ttu-id="6264e-331">Důležitější, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace je také možné nakonfigurovat zabezpečit zprávy předtím, než jsou přenosu, pomocí protokolu WS-zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="6264e-331">More important, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications can also be configured to secure the messages before they are transported, using the WS-Security protocol.</span></span> <span data-ttu-id="6264e-332">Zabezpečení právě tělo zprávy pomocí protokolu WS-Security umožňuje přenášet jako s důvěrnými napříč prostředníci před dosažením konečného cíle.</span><span class="sxs-lookup"><span data-stu-id="6264e-332">Securing just the body of a message using WS-Security allows it to be transmitted confidentially across intermediaries before reaching its final destination.</span></span>  
  
## <a name="globalization"></a><span data-ttu-id="6264e-333">Globalizace</span><span class="sxs-lookup"><span data-stu-id="6264e-333">Globalization</span></span>  
 <span data-ttu-id="6264e-334">Jazyk konfigurace ASP.NET můžete zadat jazykovou verzi pro jednotlivé služby.</span><span class="sxs-lookup"><span data-stu-id="6264e-334">The ASP.NET configuration language allows you to specify the culture for individual services.</span></span> <span data-ttu-id="6264e-335">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Nepodporuje toto nastavení konfigurace s výjimkou v režimu kompatibility ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="6264e-335">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not support that configuration setting except in ASP.NET compatibility mode.</span></span> <span data-ttu-id="6264e-336">Chcete-li lokalizovat [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služba, která nepoužívá režim kompatibility ASP.NET, zkompilovat typ služby do sestavení specifické pro jazykovou verzi a mít samostatné koncové body specifické pro jazykovou verzi pro každé sestavení specifické pro jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="6264e-336">To localize a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service that does not use ASP.NET compatibility mode, compile the service type into culture-specific assemblies, and have separate culture-specific endpoints for each culture-specific assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6264e-337">Viz také</span><span class="sxs-lookup"><span data-stu-id="6264e-337">See Also</span></span>  
 [<span data-ttu-id="6264e-338">Porovnání webových služeb ASP.NET se službou WCF na základě účelu a používaných standardů</span><span class="sxs-lookup"><span data-stu-id="6264e-338">Comparing ASP.NET Web Services to WCF Based on Purpose and Standards Used</span></span>](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used.md)
