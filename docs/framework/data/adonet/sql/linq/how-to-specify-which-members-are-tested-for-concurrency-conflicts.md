---
title: 'Postupy: Určení, kdy se mají členové testovat na konflikty souběžnosti'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d2cda293-1e2f-4878-af0e-5aaf0d092120
ms.openlocfilehash: fc6fafa474805c2644bb2deabdceed192776ac76
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938757"
---
# <a name="how-to-specify-which-members-are-tested-for-concurrency-conflicts"></a><span data-ttu-id="514fe-102">Postupy: Určení, kdy se mají členové testovat na konflikty souběžnosti</span><span class="sxs-lookup"><span data-stu-id="514fe-102">How to: Specify Which Members are Tested for Concurrency Conflicts</span></span>
<span data-ttu-id="514fe-103">Použijte jeden ze tří výčtů na [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> vlastnost u <xref:System.Data.Linq.Mapping.ColumnAttribute> atributu k určení, které členy mají být zahrnuty do kontrol aktualizací pro detekci konfliktů optimistického souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="514fe-103">Apply one of three enums to the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property on a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to specify which members are to be included in update checks for the detection of optimistic concurrency conflicts.</span></span>  
  
 <span data-ttu-id="514fe-104">Vlastnost (mapovaná v době návrhu) se používá společně s funkcemi souběžného běhu v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A></span><span class="sxs-lookup"><span data-stu-id="514fe-104">The <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property (mapped at design time) is used together with run-time concurrency features in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="514fe-105">Další informace najdete v tématu [Optimistická souběžnost: Přehled](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="514fe-105">For more information, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="514fe-106">Hodnoty původních členů jsou porovnány s aktuálním stavem databáze, pokud není určen `IsVersion=true`žádný člen.</span><span class="sxs-lookup"><span data-stu-id="514fe-106">Original member values are compared with the current database state as long as no member is designated as `IsVersion=true`.</span></span> <span data-ttu-id="514fe-107">Další informace naleznete v tématu <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span><span class="sxs-lookup"><span data-stu-id="514fe-107">For more information, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span></span>  
  
 <span data-ttu-id="514fe-108">Příklady kódu naleznete v tématu <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span><span class="sxs-lookup"><span data-stu-id="514fe-108">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span></span>  
  
### <a name="to-always-use-this-member-for-detecting-conflicts"></a><span data-ttu-id="514fe-109">Vždy používat tohoto člena k detekci konfliktů</span><span class="sxs-lookup"><span data-stu-id="514fe-109">To always use this member for detecting conflicts</span></span>  
  
1. <span data-ttu-id="514fe-110"><xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> Přidejte vlastnost<xref:System.Data.Linq.Mapping.ColumnAttribute> do atributu.</span><span class="sxs-lookup"><span data-stu-id="514fe-110">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="514fe-111">`Always`Nastavte hodnotu <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> vlastnosti na.</span><span class="sxs-lookup"><span data-stu-id="514fe-111">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property value to `Always`.</span></span>  
  
### <a name="to-never-use-this-member-for-detecting-conflicts"></a><span data-ttu-id="514fe-112">Nikdy nepoužívat tohoto člena k detekci konfliktů</span><span class="sxs-lookup"><span data-stu-id="514fe-112">To never use this member for detecting conflicts</span></span>  
  
1. <span data-ttu-id="514fe-113"><xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> Přidejte vlastnost<xref:System.Data.Linq.Mapping.ColumnAttribute> do atributu.</span><span class="sxs-lookup"><span data-stu-id="514fe-113">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="514fe-114">`Never`Nastavte hodnotu <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> vlastnosti na.</span><span class="sxs-lookup"><span data-stu-id="514fe-114">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property value to `Never`.</span></span>  
  
### <a name="to-use-this-member-for-detecting-conflicts-only-when-the-application-has-changed-the-value-of-the-member"></a><span data-ttu-id="514fe-115">Použití tohoto člena pro zjištění konfliktů pouze v případě, že aplikace změnila hodnotu člena</span><span class="sxs-lookup"><span data-stu-id="514fe-115">To use this member for detecting conflicts only when the application has changed the value of the member</span></span>  
  
1. <span data-ttu-id="514fe-116"><xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> Přidejte vlastnost<xref:System.Data.Linq.Mapping.ColumnAttribute> do atributu.</span><span class="sxs-lookup"><span data-stu-id="514fe-116">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="514fe-117">`WhenChanged`Nastavte hodnotu <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> vlastnosti na.</span><span class="sxs-lookup"><span data-stu-id="514fe-117">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property value to `WhenChanged`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="514fe-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="514fe-118">Example</span></span>  
 <span data-ttu-id="514fe-119">Následující příklad určuje, že `HomePage` objekty by nikdy neměly být testovány během kontrol aktualizací.</span><span class="sxs-lookup"><span data-stu-id="514fe-119">The following example specifies that `HomePage` objects should never be tested during update checks.</span></span> <span data-ttu-id="514fe-120">Další informace naleznete v tématu <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span><span class="sxs-lookup"><span data-stu-id="514fe-120">For more information, see <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span></span>  
  
 [!code-csharp[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.mapping.updatecheck/cs/northwind.cs#1)]
 [!code-vb[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.mapping.updatecheck/vb/northwind.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="514fe-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="514fe-121">See also</span></span>

- [<span data-ttu-id="514fe-122">Postupy: Správa konfliktů změn</span><span class="sxs-lookup"><span data-stu-id="514fe-122">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
- [<span data-ttu-id="514fe-123">Vytvoření a odeslání změn dat</span><span class="sxs-lookup"><span data-stu-id="514fe-123">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
