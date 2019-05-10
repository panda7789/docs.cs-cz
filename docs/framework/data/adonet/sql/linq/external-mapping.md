---
title: Externí mapování
ms.date: 03/30/2017
ms.assetid: 076606b8-d889-4ba0-b5da-ae577b146f23
ms.openlocfilehash: 0b6ced31f5534bd040917ecc5d241d54d9bee95f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64619715"
---
# <a name="external-mapping"></a><span data-ttu-id="dd930-102">Externí mapování</span><span class="sxs-lookup"><span data-stu-id="dd930-102">External Mapping</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="dd930-103">podporuje *externí mapování*, podle kterého použijte samostatný soubor XML pro určení mapování mezi datový model databáze a objektového modelu procesu.</span><span class="sxs-lookup"><span data-stu-id="dd930-103">supports *external mapping*, a process by which you use a separate XML file to specify mapping between the data model of the database and your object model.</span></span> <span data-ttu-id="dd930-104">Mezi výhody používání soubor externí mapování patří:</span><span class="sxs-lookup"><span data-stu-id="dd930-104">Advantages of using an external mapping file include the following:</span></span>  
  
- <span data-ttu-id="dd930-105">Abyste mohli mapování kódu mimo kód vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="dd930-105">You can keep your mapping code out of your application code.</span></span> <span data-ttu-id="dd930-106">Tento přístup snižuje nepořádku v kódu aplikace.</span><span class="sxs-lookup"><span data-stu-id="dd930-106">This approach reduces clutter in your application code.</span></span>  
  
- <span data-ttu-id="dd930-107">Můžete zpracovávat soubor externí mapování něco jako konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="dd930-107">You can treat an external mapping file something like a configuration file.</span></span> <span data-ttu-id="dd930-108">Například můžete aktualizovat, jak vaše aplikace chová po odeslání binární soubory pomocí právě výměny externí mapování souboru.</span><span class="sxs-lookup"><span data-stu-id="dd930-108">For example, you can update how your application behaves after shipping the binaries by just swapping out the external mapping file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd930-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dd930-109">Requirements</span></span>  
 <span data-ttu-id="dd930-110">Soubor mapování musí být soubor XML a souboru musí ověřovat proti [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] soubor definice (XSD) schématu.</span><span class="sxs-lookup"><span data-stu-id="dd930-110">The mapping file must be an XML file, and the file must validate against a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] schema definition (.xsd) file.</span></span>  
  
 <span data-ttu-id="dd930-111">Platí následující pravidla:</span><span class="sxs-lookup"><span data-stu-id="dd930-111">The following rules apply:</span></span>  
  
- <span data-ttu-id="dd930-112">Soubor mapování musí být soubor XML.</span><span class="sxs-lookup"><span data-stu-id="dd930-112">The mapping file must be an XML file.</span></span>  
  
- <span data-ttu-id="dd930-113">Soubor mapování XML musí být platný soubor definice schématu XML.</span><span class="sxs-lookup"><span data-stu-id="dd930-113">The XML mapping file must be valid against the XML schema definition file.</span></span> <span data-ttu-id="dd930-114">Další informace najdete v tématu [jak: Ověření DBML a externí soubory mapování](../../../../../../docs/framework/data/adonet/sql/linq/how-to-validate-dbml-and-external-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="dd930-114">For more information, see [How to: Validate DBML and External Mapping Files](../../../../../../docs/framework/data/adonet/sql/linq/how-to-validate-dbml-and-external-mapping-files.md).</span></span>  
  
- <span data-ttu-id="dd930-115">Externí mapování přepíše založených na atributech mapování.</span><span class="sxs-lookup"><span data-stu-id="dd930-115">External mapping overrides attribute-based mapping.</span></span> <span data-ttu-id="dd930-116">Jinými slovy, při použití z externí mapování zdroje k vytvoření <xref:System.Data.Linq.DataContext>, <xref:System.Data.Linq.DataContext> ignoruje všechny mapování atributy, které jste vytvořili na třídy.</span><span class="sxs-lookup"><span data-stu-id="dd930-116">In other words, when you use an external mapping source to create a <xref:System.Data.Linq.DataContext>, the <xref:System.Data.Linq.DataContext> ignores all mapping attributes you have created on classes.</span></span> <span data-ttu-id="dd930-117">Toto chování je hodnota true Určuje, zda třída je zahrnuta v externí mapování souboru.</span><span class="sxs-lookup"><span data-stu-id="dd930-117">This behavior is true whether the class is included in the external mapping file.</span></span>  
  
- [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="dd930-118">nepodporuje použití hybridních dva přístupy mapování (založených na atributech a externí).</span><span class="sxs-lookup"><span data-stu-id="dd930-118">does not support the hybrid use of the two mapping approaches (attribute-based and external).</span></span>  
  
## <a name="xml-schema-definition-file"></a><span data-ttu-id="dd930-119">Soubor definice schématu XML</span><span class="sxs-lookup"><span data-stu-id="dd930-119">XML Schema Definition File</span></span>  
 <span data-ttu-id="dd930-120">Externí mapování v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] musí být platný proti následující definici schématu XML.</span><span class="sxs-lookup"><span data-stu-id="dd930-120">External mapping in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] must be valid against the following XML schema definition.</span></span>  
  
 <span data-ttu-id="dd930-121">Tento soubor definice schématu z definičního souboru schématu, který slouží k ověření souboru DBML rozlišení.</span><span class="sxs-lookup"><span data-stu-id="dd930-121">Distinguish this schema definition file from the schema definition file that is used to validate a DBML file.</span></span> <span data-ttu-id="dd930-122">Další informace najdete v tématu [generování kódu v technologii LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)).</span><span class="sxs-lookup"><span data-stu-id="dd930-122">For more information, see [Code Generation in LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dd930-123">Uživatelé sady Visual Studio také najít tento soubor XSD v dialogovém okně schémat XML jako "LinqToSqlMapping.xsd".</span><span class="sxs-lookup"><span data-stu-id="dd930-123">Visual Studio users will also find this XSD file in the XML Schemas dialog box as "LinqToSqlMapping.xsd".</span></span> <span data-ttu-id="dd930-124">S použitím tohoto souboru správně pro ověření souboru externí mapování, naleznete v tématu [jak: Ověření DBML a externí soubory mapování](../../../../../../docs/framework/data/adonet/sql/linq/how-to-validate-dbml-and-external-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="dd930-124">To use this file correctly for validating an external mapping file, see [How to: Validate DBML and External Mapping Files](../../../../../../docs/framework/data/adonet/sql/linq/how-to-validate-dbml-and-external-mapping-files.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dd930-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dd930-125">See also</span></span>

- [<span data-ttu-id="dd930-126">Generování kódu v LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="dd930-126">Code Generation in LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [<span data-ttu-id="dd930-127">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="dd930-127">Reference</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
- [<span data-ttu-id="dd930-128">Postupy: Generování objektového modelu jako externího souboru</span><span class="sxs-lookup"><span data-stu-id="dd930-128">How to: Generate the Object Model as an External File</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-as-an-external-file.md)
