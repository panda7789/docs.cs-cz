---
title: "Externí mapování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 076606b8-d889-4ba0-b5da-ae577b146f23
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7a0650f444f901d37797ca81343f06cb566f8112
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="external-mapping"></a><span data-ttu-id="bfb76-102">Externí mapování</span><span class="sxs-lookup"><span data-stu-id="bfb76-102">External Mapping</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="bfb76-103">podporuje *externí mapování*, proces, pomocí kterého použít samostatný soubor XML pro určení mapování mezi datový model databáze a objekt modelu.</span><span class="sxs-lookup"><span data-stu-id="bfb76-103"> supports *external mapping*, a process by which you use a separate XML file to specify mapping between the data model of the database and your object model.</span></span> <span data-ttu-id="bfb76-104">Výhody používání soubor externí mapování zahrnují následující:</span><span class="sxs-lookup"><span data-stu-id="bfb76-104">Advantages of using an external mapping file include the following:</span></span>  
  
-   <span data-ttu-id="bfb76-105">Mapování kódu můžete ponechat mimo kódu aplikace.</span><span class="sxs-lookup"><span data-stu-id="bfb76-105">You can keep your mapping code out of your application code.</span></span> <span data-ttu-id="bfb76-106">Tento přístup snižuje zbytečné soubory v kódu aplikace.</span><span class="sxs-lookup"><span data-stu-id="bfb76-106">This approach reduces clutter in your application code.</span></span>  
  
-   <span data-ttu-id="bfb76-107">Lze považovat soubor externí mapování něco jako konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="bfb76-107">You can treat an external mapping file something like a configuration file.</span></span> <span data-ttu-id="bfb76-108">Například můžete aktualizovat chování aplikací po přesouvání binární soubory podle právě záměnu souboru externí mapování.</span><span class="sxs-lookup"><span data-stu-id="bfb76-108">For example, you can update how your application behaves after shipping the binaries by just swapping out the external mapping file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bfb76-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bfb76-109">Requirements</span></span>  
 <span data-ttu-id="bfb76-110">Soubor mapování musí být ve formátu XML a souboru se musí vyhodnotit proti [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] soubor schématu definice (.xsd).</span><span class="sxs-lookup"><span data-stu-id="bfb76-110">The mapping file must be an XML file, and the file must validate against a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] schema definition (.xsd) file.</span></span>  
  
 <span data-ttu-id="bfb76-111">Platí následující pravidla:</span><span class="sxs-lookup"><span data-stu-id="bfb76-111">The following rules apply:</span></span>  
  
-   <span data-ttu-id="bfb76-112">Soubor mapování musí být ve formátu XML.</span><span class="sxs-lookup"><span data-stu-id="bfb76-112">The mapping file must be an XML file.</span></span>  
  
-   <span data-ttu-id="bfb76-113">Soubor mapování XML musí být platná proti soubor definice schématu XML.</span><span class="sxs-lookup"><span data-stu-id="bfb76-113">The XML mapping file must be valid against the XML schema definition file.</span></span> <span data-ttu-id="bfb76-114">Další informace najdete v tématu [postupy: ověření DBML a externí soubory mapování](../../../../../../docs/framework/data/adonet/sql/linq/how-to-validate-dbml-and-external-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="bfb76-114">For more information, see [How to: Validate DBML and External Mapping Files](../../../../../../docs/framework/data/adonet/sql/linq/how-to-validate-dbml-and-external-mapping-files.md).</span></span>  
  
-   <span data-ttu-id="bfb76-115">Externí mapování přepsání na základě atributů mapování.</span><span class="sxs-lookup"><span data-stu-id="bfb76-115">External mapping overrides attribute-based mapping.</span></span> <span data-ttu-id="bfb76-116">Jinými slovy, při použití na externí mapování zdroj k vytvoření <xref:System.Data.Linq.DataContext>, <xref:System.Data.Linq.DataContext> ignoruje všechny atributy mapování, které jste vytvořili na třídách.</span><span class="sxs-lookup"><span data-stu-id="bfb76-116">In other words, when you use an external mapping source to create a <xref:System.Data.Linq.DataContext>, the <xref:System.Data.Linq.DataContext> ignores all mapping attributes you have created on classes.</span></span> <span data-ttu-id="bfb76-117">Toto chování je hodnota true, jestli je třída součástí souboru externí mapování.</span><span class="sxs-lookup"><span data-stu-id="bfb76-117">This behavior is true whether the class is included in the external mapping file.</span></span>  
  
-   [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="bfb76-118">nepodporuje použití hybridní dva přístupy mapování (na základě atributů a externí).</span><span class="sxs-lookup"><span data-stu-id="bfb76-118"> does not support the hybrid use of the two mapping approaches (attribute-based and external).</span></span>  
  
## <a name="xml-schema-definition-file"></a><span data-ttu-id="bfb76-119">Soubor definice schématu XML</span><span class="sxs-lookup"><span data-stu-id="bfb76-119">XML Schema Definition File</span></span>  
 <span data-ttu-id="bfb76-120">Externí mapování v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] musí být platné proti následující definice schématu XML.</span><span class="sxs-lookup"><span data-stu-id="bfb76-120">External mapping in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] must be valid against the following XML schema definition.</span></span>  
  
 <span data-ttu-id="bfb76-121">Tento soubor definice schématu z definičního souboru schématu, která je použita k ověření souboru DBML rozlišit.</span><span class="sxs-lookup"><span data-stu-id="bfb76-121">Distinguish this schema definition file from the schema definition file that is used to validate a DBML file.</span></span> <span data-ttu-id="bfb76-122">Další informace najdete v tématu [generování kódu v technologii LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)).</span><span class="sxs-lookup"><span data-stu-id="bfb76-122">For more information, see [Code Generation in LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)).</span></span>  
  
> [!NOTE]
>  [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)]<span data-ttu-id="bfb76-123">Uživatelé také najít tento soubor XSD v dialogovém okně schémat XML jako "LinqToSqlMapping.xsd".</span><span class="sxs-lookup"><span data-stu-id="bfb76-123"> users will also find this XSD file in the XML Schemas dialog box as "LinqToSqlMapping.xsd".</span></span> <span data-ttu-id="bfb76-124">Pomocí tohoto souboru správně pro ověření souboru externí mapování, najdete v části [postupy: ověření DBML a externí soubory mapování](../../../../../../docs/framework/data/adonet/sql/linq/how-to-validate-dbml-and-external-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="bfb76-124">To use this file correctly for validating an external mapping file, see [How to: Validate DBML and External Mapping Files](../../../../../../docs/framework/data/adonet/sql/linq/how-to-validate-dbml-and-external-mapping-files.md).</span></span>  
  
```  
?<?xml version="1.0" encoding="utf-16"?>  
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" targetNamespace="http://schemas.microsoft.com/linqtosql/mapping/2007" xmlns="http://schemas.microsoft.com/linqtosql/mapping/2007"  
elementFormDefault="qualified" >  
  <xs:element name="Database" type="Database" />  
  <xs:complexType name="Database">  
    <xs:sequence>  
      <xs:element name="Table" type="Table" minOccurs="0" maxOccurs="unbounded" />  
      <xs:element name="Function" type="Function" minOccurs="0" maxOccurs="unbounded" />  
    </xs:sequence>  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="Provider" type="xs:string" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Table">  
    <xs:sequence>  
      <xs:element name="Type" type="Type" minOccurs="1" maxOccurs="1" />  
    </xs:sequence>  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="Member" type="xs:string" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Type">  
    <xs:sequence>  
      <xs:choice minOccurs="0" maxOccurs="unbounded">  
        <xs:element name="Column" type="Column" minOccurs="0" maxOccurs="unbounded" />  
        <xs:element name="Association" type="Association" minOccurs="0" maxOccurs="unbounded" />  
      </xs:choice>  
      <xs:element name="Type" type="Type" minOccurs="0" maxOccurs="unbounded" />  
    </xs:sequence>  
    <xs:attribute name="Name" type="xs:string" use="required" />  
    <xs:attribute name="InheritanceCode" type="xs:string" use="optional" />  
    <xs:attribute name="IsInheritanceDefault" type="xs:boolean" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Column">  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="Member" type="xs:string" use="required" />  
    <xs:attribute name="Storage" type="xs:string" use="optional" />  
    <xs:attribute name="DbType" type="xs:string" use="optional" />  
    <xs:attribute name="IsPrimaryKey" type="xs:boolean" use="optional" />  
    <xs:attribute name="IsDbGenerated" type="xs:boolean" use="optional" />  
    <xs:attribute name="CanBeNull" type="xs:boolean" use="optional" />  
    <xs:attribute name="UpdateCheck" type="UpdateCheck" use="optional" />  
    <xs:attribute name="IsDiscriminator" type="xs:boolean" use="optional" />  
    <xs:attribute name="Expression" type="xs:string" use="optional" />  
    <xs:attribute name="IsVersion" type="xs:boolean" use="optional" />  
    <xs:attribute name="AutoSync" type="AutoSync" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Association">  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="Member" type="xs:string" use="required" />  
    <xs:attribute name="Storage" type="xs:string" use="optional" />  
    <xs:attribute name="ThisKey" type="xs:string" use="optional" />  
    <xs:attribute name="OtherKey" type="xs:string" use="optional" />  
    <xs:attribute name="IsForeignKey" type="xs:boolean" use="optional" />  
    <xs:attribute name="IsUnique" type="xs:boolean" use="optional" />  
    <xs:attribute name="DeleteRule" type="xs:string" use="optional" />  
    <xs:attribute name="DeleteOnNull" type="xs:boolean" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Function">  
    <xs:sequence>  
      <xs:element name="Parameter" type="Parameter" minOccurs="0" maxOccurs="unbounded" />  
      <xs:choice>  
        <xs:element name="ElementType" type="Type" minOccurs="0" maxOccurs="unbounded" />  
        <xs:element name="Return" type="Return" minOccurs="0" maxOccurs="1" />  
      </xs:choice>  
    </xs:sequence>  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="Method" type="xs:string" use="required" />  
    <xs:attribute name="IsComposable" type="xs:boolean" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Parameter">  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="Parameter" type="xs:string" use="required" />  
    <xs:attribute name="DbType" type="xs:string" use="optional" />  
    <xs:attribute name="Direction" type="ParameterDirection" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Return">  
    <xs:attribute name="DbType" type="xs:string" use="optional" />  
  </xs:complexType>  
  <xs:simpleType name="UpdateCheck">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="Always" />  
      <xs:enumeration value="Never" />  
      <xs:enumeration value="WhenChanged" />  
    </xs:restriction>  
  </xs:simpleType>  
  <xs:simpleType name="ParameterDirection">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="In" />  
      <xs:enumeration value="Out" />  
      <xs:enumeration value="InOut" />  
    </xs:restriction>  
  </xs:simpleType>  
  <xs:simpleType name="AutoSync">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="Never" />  
      <xs:enumeration value="OnInsert" />  
      <xs:enumeration value="OnUpdate" />  
      <xs:enumeration value="Always" />  
      <xs:enumeration value="Default" />  
    </xs:restriction>  
  </xs:simpleType>  
</xs:schema>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bfb76-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="bfb76-125">See Also</span></span>  
 [<span data-ttu-id="bfb76-126">Generování kódu v technologii LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="bfb76-126">Code Generation in LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)  
 [<span data-ttu-id="bfb76-127">Referenční dokumentace</span><span class="sxs-lookup"><span data-stu-id="bfb76-127">Reference</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)  
 [<span data-ttu-id="bfb76-128">Postupy: generování objektový Model jako externí soubor</span><span class="sxs-lookup"><span data-stu-id="bfb76-128">How to: Generate the Object Model as an External File</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-as-an-external-file.md)
