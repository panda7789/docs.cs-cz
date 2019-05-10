---
title: Mapování omezení schématu XML (XSD) k omezením datové sady
ms.date: 03/30/2017
ms.assetid: 3d0d1a4b-9104-434f-ac04-6c01ab5716b5
ms.openlocfilehash: cdbfba96c4cfe52cfbd58246be60842540a84754
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64604003"
---
# <a name="mapping-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="d8b49-102">Mapování omezení schématu XML (XSD) k omezením datové sady</span><span class="sxs-lookup"><span data-stu-id="d8b49-102">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="d8b49-103">Schéma XML definice jazyk (XSD) umožňuje zadat pro prvky a atributy, které definuje omezení.</span><span class="sxs-lookup"><span data-stu-id="d8b49-103">The XML Schema definition language (XSD) allows constraints to be specified on the elements and attributes it defines.</span></span> <span data-ttu-id="d8b49-104">Při mapování schématu XML na relační schéma v <xref:System.Data.DataSet>, omezení schématu XML se mapují na odpovídající omezení relačních tabulek a sloupců v rámci **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="d8b49-104">When mapping an XML Schema to relational schema in a <xref:System.Data.DataSet>, XML Schema constraints are mapped to appropriate relational constraints on the tables and columns within the **DataSet**.</span></span>  
  
 <span data-ttu-id="d8b49-105">Tato část pojednává o mapování následující omezení schématu XML:</span><span class="sxs-lookup"><span data-stu-id="d8b49-105">This section discusses the mapping of the following XML Schema constraints:</span></span>  
  
- <span data-ttu-id="d8b49-106">Omezení jedinečnosti zadat pomocí **jedinečný** elementu.</span><span class="sxs-lookup"><span data-stu-id="d8b49-106">The uniqueness constraint specified using the **unique** element.</span></span>  
  
- <span data-ttu-id="d8b49-107">Omezení pro klíč zadaný pomocí **klíč** elementu.</span><span class="sxs-lookup"><span data-stu-id="d8b49-107">The key constraint specified using the **key** element.</span></span>  
  
- <span data-ttu-id="d8b49-108">Omezení keyref zadat pomocí **keyref** elementu.</span><span class="sxs-lookup"><span data-stu-id="d8b49-108">The keyref constraint specified using the **keyref** element.</span></span>  
  
 <span data-ttu-id="d8b49-109">Pomocí omezení na elementu nebo atributu zadejte určitá omezení na hodnoty elementu v žádné instanci dokumentu.</span><span class="sxs-lookup"><span data-stu-id="d8b49-109">By using a constraint on an element or attribute, you specify certain restrictions on the values of the element in any instance of the document.</span></span> <span data-ttu-id="d8b49-110">Například klíče omezení na **CustomerID** podřízený prvek **zákazníka** element ve schématu znamená, že hodnoty **CustomerID** musí být podřízený element Jedinečný v žádné instanci dokumentu, a že nejsou povoleny hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="d8b49-110">For example, a key constraint on a **CustomerID** child element of a **Customer** element in the schema indicates that the values of the **CustomerID** child element must be unique in any document instance, and that null values are not allowed.</span></span>  
  
 <span data-ttu-id="d8b49-111">Omezení je taky možné specifikovat mezi elementy a atributy v dokumentu, aby bylo možné navázat relaci v rámci dokumentu.</span><span class="sxs-lookup"><span data-stu-id="d8b49-111">Constraints can also be specified between elements and attributes in a document, in order to establish a relationship within the document.</span></span> <span data-ttu-id="d8b49-112">Key ani keyref omezení se používají ve schématu zadat omezení v rámci dokumentu, výsledkem je vztah mezi dokumentu elementů a atributů.</span><span class="sxs-lookup"><span data-stu-id="d8b49-112">The key and keyref constraints are used in the schema to specify the constraints within the document, resulting in a relationship between document elements and attributes.</span></span>  
  
 <span data-ttu-id="d8b49-113">Proces mapování převede odpovídající omezení u tabulky vytvořené v rámci těchto omezení schématu **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="d8b49-113">The mapping process converts these schema constraints into appropriate constraints on the tables created within the **DataSet**.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d8b49-114">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="d8b49-114">In This Section</span></span>  
 [<span data-ttu-id="d8b49-115">Mapování jedinečných omezení schématu XML (XSD) k omezením datové sady</span><span class="sxs-lookup"><span data-stu-id="d8b49-115">Map unique XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-unique-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="d8b49-116">Popisuje prvky schématu XML použitý k vytvoření jedinečné omezení **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="d8b49-116">Describes the XML Schema elements used to create unique constraints in a **DataSet**.</span></span>  
  
 [<span data-ttu-id="d8b49-117">Mapování klíčových omezení schématu XML (XSD) k omezením datové sady</span><span class="sxs-lookup"><span data-stu-id="d8b49-117">Map key XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-key-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="d8b49-118">Popisuje prvky schématu XML použitý k vytvoření omezení klíče (jedinečná omezení kde nejsou povoleny hodnoty null) **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="d8b49-118">Describes the XML Schema elements used to create key constraints (unique constraints where null values are not allowed) in a **DataSet**.</span></span>  
  
 [<span data-ttu-id="d8b49-119">Mapování klíčových referenčních omezení schématu XML (XSD) k omezením datové sady</span><span class="sxs-lookup"><span data-stu-id="d8b49-119">Map keyref XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-keyref-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="d8b49-120">Popisuje prvky schématu XML použitý k vytvoření keyref omezení (cizí klíč) **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="d8b49-120">Describes the XML Schema elements used to create keyref (foreign key) constraints in a **DataSet**.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d8b49-121">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="d8b49-121">Related Sections</span></span>  
 [<span data-ttu-id="d8b49-122">Odvozování relační struktury datové sady ze schématu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="d8b49-122">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 <span data-ttu-id="d8b49-123">Popisuje relační struktury nebo schématu, **datovou sadu** , který je vytvořen ze schématu XSD.</span><span class="sxs-lookup"><span data-stu-id="d8b49-123">Describes the relational structure, or schema, of a **DataSet** that is created from XSD schema.</span></span>  
  
 [<span data-ttu-id="d8b49-124">Generování relací datové sady ze schématu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="d8b49-124">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 <span data-ttu-id="d8b49-125">Popisuje prvky schématu XML použitý k vytvoření relace mezi sloupci tabulky v **datovou sadu**.</span><span class="sxs-lookup"><span data-stu-id="d8b49-125">Describes the XML Schema elements used to create relations between table columns in a **DataSet**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8b49-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d8b49-126">See also</span></span>

- [<span data-ttu-id="d8b49-127">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="d8b49-127">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
