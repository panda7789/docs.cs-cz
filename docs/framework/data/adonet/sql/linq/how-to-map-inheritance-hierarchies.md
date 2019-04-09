---
title: 'Postupy: Mapování hierarchií dědičnosti'
ms.date: 03/30/2017
ms.assetid: b27c779b-9355-4dc7-b95f-7dfd504b6e48
dev_langs:
- csharp
- vb
ms.openlocfilehash: f75c7fe701c4a2fab1f993517828b38e5a26e2bd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59138083"
---
# <a name="how-to-map-inheritance-hierarchies"></a><span data-ttu-id="8a2d1-102">Postupy: Mapování hierarchií dědičnosti</span><span class="sxs-lookup"><span data-stu-id="8a2d1-102">How to: Map Inheritance Hierarchies</span></span>
<span data-ttu-id="8a2d1-103">Implementace dědičnosti mapování v [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)], musíte zadat atributy a atribut vlastnosti ve třídě kořenové hierarchii dědičnosti jak je popsáno v následujících krocích.</span><span class="sxs-lookup"><span data-stu-id="8a2d1-103">To implement inheritance mapping in [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)], you must specify the attributes and attribute properties on the root class of the inheritance hierarchy as described in the following steps.</span></span> <span data-ttu-id="8a2d1-104">Pomocí sady Visual Studio mohou vývojáři [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] mapování hierarchií dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="8a2d1-104">Developers using Visual Studio can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to map inheritance hierarchies.</span></span> <span data-ttu-id="8a2d1-105">Zobrazit [jak: Konfigurace dědičnosti pomocí Návrháře relací objektů](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer).</span><span class="sxs-lookup"><span data-stu-id="8a2d1-105">See [How to: Configure inheritance by using the O/R Designer](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8a2d1-106">V podtříd jsou požadována žádná speciální atributy nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="8a2d1-106">No special attributes or properties are required on the subclasses.</span></span> <span data-ttu-id="8a2d1-107">Mějte na paměti zvlášť, podtřídy nemají <xref:System.Data.Linq.Mapping.TableAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="8a2d1-107">Note especially that subclasses do not have the <xref:System.Data.Linq.Mapping.TableAttribute> attribute.</span></span>  
  
### <a name="to-map-an-inheritance-hierarchy"></a><span data-ttu-id="8a2d1-108">Mapování hierarchie dědičnosti</span><span class="sxs-lookup"><span data-stu-id="8a2d1-108">To map an inheritance hierarchy</span></span>  
  
1.  <span data-ttu-id="8a2d1-109">Přidat <xref:System.Data.Linq.Mapping.TableAttribute> atribut kořenový třídy.</span><span class="sxs-lookup"><span data-stu-id="8a2d1-109">Add the <xref:System.Data.Linq.Mapping.TableAttribute> attribute to the root class.</span></span>  
  
2.  <span data-ttu-id="8a2d1-110">Také do kořenové třídy, přidejte <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> atribut pro každou třídu ve struktuře hierarchie.</span><span class="sxs-lookup"><span data-stu-id="8a2d1-110">Also to the root class, add an <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attribute for each class in the hierarchy structure.</span></span>  
  
3.  <span data-ttu-id="8a2d1-111">Pro každou <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> atribut, definovat <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="8a2d1-111">For each <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attribute, define a <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> property.</span></span>  
  
     <span data-ttu-id="8a2d1-112">Tato vlastnost obsahuje hodnotu, která se zobrazí v tabulce databáze <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> sloupec, aby označoval, které třída nebo podtřídou tento řádek dat patří do.</span><span class="sxs-lookup"><span data-stu-id="8a2d1-112">This property holds a value that appears in the database table in the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> column to indicate which class or subclass this row of data belongs to.</span></span>  
  
4.  <span data-ttu-id="8a2d1-113">Pro každou <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> atribut, také přidat <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="8a2d1-113">For each <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attribute, also add a <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A> property.</span></span>  
  
     <span data-ttu-id="8a2d1-114">Tato vlastnost obsahuje hodnotu, která určuje, které třída nebo podtřídou označuje hodnotu klíče.</span><span class="sxs-lookup"><span data-stu-id="8a2d1-114">This property holds a value that specifies which class or subclass the key value signifies.</span></span>  
  
5.  <span data-ttu-id="8a2d1-115">Pouze na jednom z <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> atributy, přidejte <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="8a2d1-115">On only one of the <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attributes, add an <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A> property.</span></span>  
  
     <span data-ttu-id="8a2d1-116">Tato vlastnost slouží k určení *záložní* mapování, když hodnota diskriminátoru z databázové tabulky neodpovídá žádnému <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> hodnotu v mapování dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="8a2d1-116">This property serves to designate a *fallback* mapping when the discriminator value from the database table does not match any <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> value in the inheritance mappings.</span></span>  
  
6.  <span data-ttu-id="8a2d1-117">Přidat <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> vlastnost <xref:System.Data.Linq.Mapping.ColumnAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="8a2d1-117">Add an <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> property for a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
     <span data-ttu-id="8a2d1-118">Tato vlastnost znamená, že se jedná o sloupec, který obsahuje <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="8a2d1-118">This property signifies that this is the column that holds the <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a2d1-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="8a2d1-119">Example</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8a2d1-120">Pokud používáte Visual Studio, můžete použít [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] konfigurace dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="8a2d1-120">If you are using Visual Studio, you can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to configure inheritance.</span></span> <span data-ttu-id="8a2d1-121">Zobrazit [jak: Konfigurace dědičnosti pomocí Návrháře relací objektů](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)</span><span class="sxs-lookup"><span data-stu-id="8a2d1-121">See [How to: Configure inheritance by using the O/R Designer](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)</span></span>  
  
 <span data-ttu-id="8a2d1-122">V následujícím příkladu kódu `Vehicle` je definován jako kořenová třída a byly implementovány v předchozích krocích k popisu hierarchii [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8a2d1-122">In the following code example, `Vehicle` is defined as the root class, and the previous steps have been implemented to describe the hierarchy for [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span></span>  
  
 [!code-csharp[DLinqCustomize#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#4)]
 [!code-vb[DLinqCustomize#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="8a2d1-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8a2d1-123">See also</span></span>

- [<span data-ttu-id="8a2d1-124">Podpora dědičnosti</span><span class="sxs-lookup"><span data-stu-id="8a2d1-124">Inheritance Support</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/inheritance-support.md)
- [<span data-ttu-id="8a2d1-125">Postupy: Přizpůsobení tříd entit pomocí editoru kódu</span><span class="sxs-lookup"><span data-stu-id="8a2d1-125">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
