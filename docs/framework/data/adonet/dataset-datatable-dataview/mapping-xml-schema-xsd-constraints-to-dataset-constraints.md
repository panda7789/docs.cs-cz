---
title: Mapování omezení schématu XML (XSD) k omezením datové sady
ms.date: 03/30/2017
ms.assetid: 3d0d1a4b-9104-434f-ac04-6c01ab5716b5
ms.openlocfilehash: b44c3193e1b9e2e52e086111eab0ab0b0cae5c97
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786071"
---
# <a name="mapping-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="9c0ce-102">Mapování omezení schématu XML (XSD) k omezením datové sady</span><span class="sxs-lookup"><span data-stu-id="9c0ce-102">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="9c0ce-103">Jazyk definice schématu XML (XSD) umožňuje určení omezení pro prvky a atributy, které definuje.</span><span class="sxs-lookup"><span data-stu-id="9c0ce-103">The XML Schema definition language (XSD) allows constraints to be specified on the elements and attributes it defines.</span></span> <span data-ttu-id="9c0ce-104">Při mapování schématu XML na relační schéma v <xref:System.Data.DataSet>, jsou omezení schématu XML mapována na odpovídající relační omezení pro tabulky a sloupce v rámci **datové sady**.</span><span class="sxs-lookup"><span data-stu-id="9c0ce-104">When mapping an XML Schema to relational schema in a <xref:System.Data.DataSet>, XML Schema constraints are mapped to appropriate relational constraints on the tables and columns within the **DataSet**.</span></span>  
  
 <span data-ttu-id="9c0ce-105">Tato část popisuje mapování následujících omezení schématu XML:</span><span class="sxs-lookup"><span data-stu-id="9c0ce-105">This section discusses the mapping of the following XML Schema constraints:</span></span>  
  
- <span data-ttu-id="9c0ce-106">Omezení jedinečnosti zadané pomocí **jedinečného** prvku.</span><span class="sxs-lookup"><span data-stu-id="9c0ce-106">The uniqueness constraint specified using the **unique** element.</span></span>  
  
- <span data-ttu-id="9c0ce-107">Omezení klíče zadané pomocí **klíčového** elementu.</span><span class="sxs-lookup"><span data-stu-id="9c0ce-107">The key constraint specified using the **key** element.</span></span>  
  
- <span data-ttu-id="9c0ce-108">Omezení keyref zadané pomocí elementu **keyref**</span><span class="sxs-lookup"><span data-stu-id="9c0ce-108">The keyref constraint specified using the **keyref** element.</span></span>  
  
 <span data-ttu-id="9c0ce-109">Pomocí omezení pro element nebo atribut zadáte určitá omezení pro hodnoty prvku v jakékoli instanci dokumentu.</span><span class="sxs-lookup"><span data-stu-id="9c0ce-109">By using a constraint on an element or attribute, you specify certain restrictions on the values of the element in any instance of the document.</span></span> <span data-ttu-id="9c0ce-110">Například omezení klíče u podřízeného prvku **KódZákazníka** elementu **Customer** ve schématu označuje, že hodnoty podřízeného prvku **KódZákazníka** musí být jedinečné v jakékoli instanci dokumentu a že hodnoty null nejsou povoleny.</span><span class="sxs-lookup"><span data-stu-id="9c0ce-110">For example, a key constraint on a **CustomerID** child element of a **Customer** element in the schema indicates that the values of the **CustomerID** child element must be unique in any document instance, and that null values are not allowed.</span></span>  
  
 <span data-ttu-id="9c0ce-111">Omezení lze také zadat mezi elementy a atributy v dokumentu, aby bylo možné vytvořit relaci v rámci dokumentu.</span><span class="sxs-lookup"><span data-stu-id="9c0ce-111">Constraints can also be specified between elements and attributes in a document, in order to establish a relationship within the document.</span></span> <span data-ttu-id="9c0ce-112">Omezení Key a keyref se používají ve schématu k určení omezení v rámci dokumentu, což má za následek relaci mezi prvky dokumentu a atributy.</span><span class="sxs-lookup"><span data-stu-id="9c0ce-112">The key and keyref constraints are used in the schema to specify the constraints within the document, resulting in a relationship between document elements and attributes.</span></span>  
  
 <span data-ttu-id="9c0ce-113">Proces mapování převede Tato omezení schématu na vhodná omezení pro tabulky vytvořené v rámci **datové sady**.</span><span class="sxs-lookup"><span data-stu-id="9c0ce-113">The mapping process converts these schema constraints into appropriate constraints on the tables created within the **DataSet**.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9c0ce-114">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="9c0ce-114">In This Section</span></span>  
 [<span data-ttu-id="9c0ce-115">Mapování jedinečných omezení schématu XML (XSD) k omezením datové sady</span><span class="sxs-lookup"><span data-stu-id="9c0ce-115">Map unique XML Schema (XSD) Constraints to DataSet Constraints</span></span>](map-unique-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="9c0ce-116">Popisuje prvky schématu XML používané k vytváření jedinečných omezení v **datové sadě**.</span><span class="sxs-lookup"><span data-stu-id="9c0ce-116">Describes the XML Schema elements used to create unique constraints in a **DataSet**.</span></span>  
  
 [<span data-ttu-id="9c0ce-117">Mapování klíčových omezení schématu XML (XSD) k omezením datové sady</span><span class="sxs-lookup"><span data-stu-id="9c0ce-117">Map key XML Schema (XSD) Constraints to DataSet Constraints</span></span>](map-key-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="9c0ce-118">Popisuje prvky schématu XML, které se používají k vytvoření omezení klíče (jedinečná omezení, kde nejsou povoleny hodnoty null) v **datové sadě**.</span><span class="sxs-lookup"><span data-stu-id="9c0ce-118">Describes the XML Schema elements used to create key constraints (unique constraints where null values are not allowed) in a **DataSet**.</span></span>  
  
 [<span data-ttu-id="9c0ce-119">Mapování klíčových referenčních omezení schématu XML (XSD) k omezením datové sady</span><span class="sxs-lookup"><span data-stu-id="9c0ce-119">Map keyref XML Schema (XSD) Constraints to DataSet Constraints</span></span>](map-keyref-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="9c0ce-120">Popisuje prvky schématu XML používané k vytvoření omezení keyref (cizí klíč) v **datové sadě**.</span><span class="sxs-lookup"><span data-stu-id="9c0ce-120">Describes the XML Schema elements used to create keyref (foreign key) constraints in a **DataSet**.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9c0ce-121">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="9c0ce-121">Related Sections</span></span>  
 [<span data-ttu-id="9c0ce-122">Odvozování relační struktury datové sady ze schématu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="9c0ce-122">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 <span data-ttu-id="9c0ce-123">Popisuje relační strukturu neboli schéma pro **datovou sadu** , která je vytvořena ze schématu XSD.</span><span class="sxs-lookup"><span data-stu-id="9c0ce-123">Describes the relational structure, or schema, of a **DataSet** that is created from XSD schema.</span></span>  
  
 [<span data-ttu-id="9c0ce-124">Generování relací datové sady ze schématu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="9c0ce-124">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)  
 <span data-ttu-id="9c0ce-125">Popisuje prvky schématu XML, které slouží k vytvoření vztahů mezi sloupci tabulky v **datové sadě**.</span><span class="sxs-lookup"><span data-stu-id="9c0ce-125">Describes the XML Schema elements used to create relations between table columns in a **DataSet**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c0ce-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9c0ce-126">See also</span></span>

- [<span data-ttu-id="9c0ce-127">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="9c0ce-127">ADO.NET Overview</span></span>](../ado-net-overview.md)
