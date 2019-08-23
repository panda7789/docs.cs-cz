---
title: 'Postupy: Mapování hierarchií dědičnosti'
ms.date: 03/30/2017
ms.assetid: b27c779b-9355-4dc7-b95f-7dfd504b6e48
dev_langs:
- csharp
- vb
ms.openlocfilehash: 618abc8e681a6f43a1054d0ca2cec2fbdec853f5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943565"
---
# <a name="how-to-map-inheritance-hierarchies"></a><span data-ttu-id="9b193-102">Postupy: Mapování hierarchií dědičnosti</span><span class="sxs-lookup"><span data-stu-id="9b193-102">How to: Map Inheritance Hierarchies</span></span>
<span data-ttu-id="9b193-103">Chcete-li implementovat mapování [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)]dědičnosti v nástroji, je nutné zadat atributy a vlastnosti atributu pro kořenovou třídu Hierarchie dědičnosti, jak je popsáno v následujícím postupu.</span><span class="sxs-lookup"><span data-stu-id="9b193-103">To implement inheritance mapping in [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)], you must specify the attributes and attribute properties on the root class of the inheritance hierarchy as described in the following steps.</span></span> <span data-ttu-id="9b193-104">Vývojáři, kteří používají Visual Studio, mohou použít Návrhář relací objektů k mapování hierarchií dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="9b193-104">Developers using Visual Studio can use the Object Relational Designer to map inheritance hierarchies.</span></span> <span data-ttu-id="9b193-105">Viz [jak: Nakonfigurujte dědičnost pomocí návrháře](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)O/R.</span><span class="sxs-lookup"><span data-stu-id="9b193-105">See [How to: Configure inheritance by using the O/R Designer](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9b193-106">U podtříd nejsou vyžadovány žádné speciální atributy ani vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="9b193-106">No special attributes or properties are required on the subclasses.</span></span> <span data-ttu-id="9b193-107">Všimněte si, že podtřídy <xref:System.Data.Linq.Mapping.TableAttribute> nemají atribut.</span><span class="sxs-lookup"><span data-stu-id="9b193-107">Note especially that subclasses do not have the <xref:System.Data.Linq.Mapping.TableAttribute> attribute.</span></span>  
  
### <a name="to-map-an-inheritance-hierarchy"></a><span data-ttu-id="9b193-108">Mapování hierarchie dědičnosti</span><span class="sxs-lookup"><span data-stu-id="9b193-108">To map an inheritance hierarchy</span></span>  
  
1. <span data-ttu-id="9b193-109"><xref:System.Data.Linq.Mapping.TableAttribute> Přidejte atribut do kořenové třídy.</span><span class="sxs-lookup"><span data-stu-id="9b193-109">Add the <xref:System.Data.Linq.Mapping.TableAttribute> attribute to the root class.</span></span>  
  
2. <span data-ttu-id="9b193-110">Také pro kořenovou třídu přidejte <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> atribut pro každou třídu v hierarchii struktury.</span><span class="sxs-lookup"><span data-stu-id="9b193-110">Also to the root class, add an <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attribute for each class in the hierarchy structure.</span></span>  
  
3. <span data-ttu-id="9b193-111">Pro každý <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> atribut <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> definujte vlastnost.</span><span class="sxs-lookup"><span data-stu-id="9b193-111">For each <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attribute, define a <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> property.</span></span>  
  
     <span data-ttu-id="9b193-112">Tato vlastnost obsahuje hodnotu, která se zobrazí v databázové tabulce ve <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> sloupci, aby označovala třídu nebo podtřídu, do které tento řádek dat patří.</span><span class="sxs-lookup"><span data-stu-id="9b193-112">This property holds a value that appears in the database table in the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> column to indicate which class or subclass this row of data belongs to.</span></span>  
  
4. <span data-ttu-id="9b193-113">Pro každý <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> atribut také <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A> přidejte vlastnost.</span><span class="sxs-lookup"><span data-stu-id="9b193-113">For each <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attribute, also add a <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A> property.</span></span>  
  
     <span data-ttu-id="9b193-114">Tato vlastnost obsahuje hodnotu, která určuje třídu nebo podtřídu hodnoty klíče.</span><span class="sxs-lookup"><span data-stu-id="9b193-114">This property holds a value that specifies which class or subclass the key value signifies.</span></span>  
  
5. <span data-ttu-id="9b193-115">Pouze v jednom z <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> atributů <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A> přidejte vlastnost.</span><span class="sxs-lookup"><span data-stu-id="9b193-115">On only one of the <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attributes, add an <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A> property.</span></span>  
  
     <span data-ttu-id="9b193-116">Tato vlastnost slouží k určení *záložního* mapování, pokud hodnota diskriminátoru z tabulky databáze neodpovídá žádné <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> hodnotě v mapování dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="9b193-116">This property serves to designate a *fallback* mapping when the discriminator value from the database table does not match any <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> value in the inheritance mappings.</span></span>  
  
6. <span data-ttu-id="9b193-117"><xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> Přidejte vlastnost<xref:System.Data.Linq.Mapping.ColumnAttribute> pro atribut.</span><span class="sxs-lookup"><span data-stu-id="9b193-117">Add an <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> property for a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
     <span data-ttu-id="9b193-118">Tato vlastnost znamená, že se jedná o sloupec, který obsahuje <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="9b193-118">This property signifies that this is the column that holds the <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9b193-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="9b193-119">Example</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9b193-120">Pokud používáte aplikaci Visual Studio, můžete použít Návrhář relací objektů ke konfiguraci dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="9b193-120">If you are using Visual Studio, you can use the Object Relational Designer to configure inheritance.</span></span> <span data-ttu-id="9b193-121">Viz [jak: Konfigurace dědičnosti pomocí Návrháře relací objektů](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)</span><span class="sxs-lookup"><span data-stu-id="9b193-121">See [How to: Configure inheritance by using the O/R Designer](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)</span></span>  
  
 <span data-ttu-id="9b193-122">V následujícím příkladu `Vehicle` kódu je definován jako kořenová třída a předchozí kroky byly implementovány pro popis hierarchie pro [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9b193-122">In the following code example, `Vehicle` is defined as the root class, and the previous steps have been implemented to describe the hierarchy for [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span></span>  
  
 [!code-csharp[DLinqCustomize#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#4)]
 [!code-vb[DLinqCustomize#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="9b193-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9b193-123">See also</span></span>

- [<span data-ttu-id="9b193-124">Podpora dědičnosti</span><span class="sxs-lookup"><span data-stu-id="9b193-124">Inheritance Support</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/inheritance-support.md)
- [<span data-ttu-id="9b193-125">Postupy: Přizpůsobení tříd entit pomocí editoru kódu</span><span class="sxs-lookup"><span data-stu-id="9b193-125">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
