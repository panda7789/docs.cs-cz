---
title: 'Postupy: mapování hierarchií dědičnosti'
ms.date: 03/30/2017
ms.assetid: b27c779b-9355-4dc7-b95f-7dfd504b6e48
dev_langs:
- csharp
- vb
ms.openlocfilehash: 737cb8743d8fd9c93cd46ebf50fba3fe554a35f2
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634661"
---
# <a name="how-to-map-inheritance-hierarchies"></a><span data-ttu-id="8e958-102">Postupy: mapování hierarchií dědičnosti</span><span class="sxs-lookup"><span data-stu-id="8e958-102">How to: Map Inheritance Hierarchies</span></span>
<span data-ttu-id="8e958-103">Chcete-li implementovat mapování dědičnosti v technologii LINQ, je nutné zadat atributy a vlastnosti atributu v kořenové třídě hierarchie dědičnosti, jak je popsáno v následujícím postupu.</span><span class="sxs-lookup"><span data-stu-id="8e958-103">To implement inheritance mapping in LINQ, you must specify the attributes and attribute properties on the root class of the inheritance hierarchy as described in the following steps.</span></span> <span data-ttu-id="8e958-104">Vývojáři, kteří používají Visual Studio, mohou použít Návrhář relací objektů k mapování hierarchií dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="8e958-104">Developers using Visual Studio can use the Object Relational Designer to map inheritance hierarchies.</span></span> <span data-ttu-id="8e958-105">Viz [How to: Configure dědičnost pomocí návrháře o/R](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer).</span><span class="sxs-lookup"><span data-stu-id="8e958-105">See [How to: Configure inheritance by using the O/R Designer](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8e958-106">U podtříd nejsou vyžadovány žádné speciální atributy ani vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="8e958-106">No special attributes or properties are required on the subclasses.</span></span> <span data-ttu-id="8e958-107">Všimněte si, že podtřídy nemají atribut <xref:System.Data.Linq.Mapping.TableAttribute>.</span><span class="sxs-lookup"><span data-stu-id="8e958-107">Note especially that subclasses do not have the <xref:System.Data.Linq.Mapping.TableAttribute> attribute.</span></span>  
  
### <a name="to-map-an-inheritance-hierarchy"></a><span data-ttu-id="8e958-108">Mapování hierarchie dědičnosti</span><span class="sxs-lookup"><span data-stu-id="8e958-108">To map an inheritance hierarchy</span></span>  
  
1. <span data-ttu-id="8e958-109">Přidejte atribut <xref:System.Data.Linq.Mapping.TableAttribute> do kořenové třídy.</span><span class="sxs-lookup"><span data-stu-id="8e958-109">Add the <xref:System.Data.Linq.Mapping.TableAttribute> attribute to the root class.</span></span>  
  
2. <span data-ttu-id="8e958-110">Také na kořenovou třídu přidejte atribut <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> pro každou třídu ve struktuře hierarchie.</span><span class="sxs-lookup"><span data-stu-id="8e958-110">Also to the root class, add an <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attribute for each class in the hierarchy structure.</span></span>  
  
3. <span data-ttu-id="8e958-111">Pro každý atribut <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> definujte vlastnost <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A>.</span><span class="sxs-lookup"><span data-stu-id="8e958-111">For each <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attribute, define a <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> property.</span></span>  
  
     <span data-ttu-id="8e958-112">Tato vlastnost obsahuje hodnotu, která se zobrazí v databázové tabulce ve sloupci <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A>, aby označovala třídu nebo podtřídou, do které tento řádek dat patří.</span><span class="sxs-lookup"><span data-stu-id="8e958-112">This property holds a value that appears in the database table in the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> column to indicate which class or subclass this row of data belongs to.</span></span>  
  
4. <span data-ttu-id="8e958-113">U každého atributu <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> přidejte také vlastnost <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A>.</span><span class="sxs-lookup"><span data-stu-id="8e958-113">For each <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attribute, also add a <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A> property.</span></span>  
  
     <span data-ttu-id="8e958-114">Tato vlastnost obsahuje hodnotu, která určuje třídu nebo podtřídu hodnoty klíče.</span><span class="sxs-lookup"><span data-stu-id="8e958-114">This property holds a value that specifies which class or subclass the key value signifies.</span></span>  
  
5. <span data-ttu-id="8e958-115">Pouze na jednom z atributů <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> přidejte vlastnost <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A>.</span><span class="sxs-lookup"><span data-stu-id="8e958-115">On only one of the <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attributes, add an <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A> property.</span></span>  
  
     <span data-ttu-id="8e958-116">Tato vlastnost slouží k určení *záložního* mapování, pokud hodnota diskriminátoru z tabulky databáze neodpovídá žádné <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> hodnotě v mapování dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="8e958-116">This property serves to designate a *fallback* mapping when the discriminator value from the database table does not match any <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> value in the inheritance mappings.</span></span>  
  
6. <span data-ttu-id="8e958-117">Přidejte vlastnost <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> pro atribut <xref:System.Data.Linq.Mapping.ColumnAttribute>.</span><span class="sxs-lookup"><span data-stu-id="8e958-117">Add an <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> property for a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
     <span data-ttu-id="8e958-118">Tato vlastnost znamená, že se jedná o sloupec, který obsahuje hodnotu <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A>.</span><span class="sxs-lookup"><span data-stu-id="8e958-118">This property signifies that this is the column that holds the <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e958-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="8e958-119">Example</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8e958-120">Pokud používáte aplikaci Visual Studio, můžete použít Návrhář relací objektů ke konfiguraci dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="8e958-120">If you are using Visual Studio, you can use the Object Relational Designer to configure inheritance.</span></span> <span data-ttu-id="8e958-121">Viz [Postupy: Konfigurace dědičnosti pomocí návrháře O/R](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)</span><span class="sxs-lookup"><span data-stu-id="8e958-121">See [How to: Configure inheritance by using the O/R Designer](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)</span></span>  
  
 <span data-ttu-id="8e958-122">V následujícím příkladu kódu je `Vehicle` definováno jako kořenová třída a předchozí kroky byly implementovány pro popis hierarchie pro technologii LINQ.</span><span class="sxs-lookup"><span data-stu-id="8e958-122">In the following code example, `Vehicle` is defined as the root class, and the previous steps have been implemented to describe the hierarchy for LINQ.</span></span>  
  
 [!code-csharp[DLinqCustomize#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#4)]
 [!code-vb[DLinqCustomize#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="8e958-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8e958-123">See also</span></span>

- [<span data-ttu-id="8e958-124">Podpora dědičnosti</span><span class="sxs-lookup"><span data-stu-id="8e958-124">Inheritance Support</span></span>](inheritance-support.md)
- [<span data-ttu-id="8e958-125">Postupy: Přizpůsobení tříd entit pomocí editoru kódu</span><span class="sxs-lookup"><span data-stu-id="8e958-125">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
