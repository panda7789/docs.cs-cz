---
title: 'Postupy: Znázornění primárních klíčů'
ms.date: 03/30/2017
ms.assetid: 63c65289-6539-42b2-8493-891c232018fa
ms.openlocfilehash: 28c62798f965edfcffe1a156213c2481a8193b49
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943530"
---
# <a name="how-to-represent-primary-keys"></a><span data-ttu-id="0b0da-102">Postupy: Znázornění primárních klíčů</span><span class="sxs-lookup"><span data-stu-id="0b0da-102">How to: Represent Primary Keys</span></span>
<span data-ttu-id="0b0da-103">Pomocí vlastnosti u<xref:System.Data.Linq.Mapping.ColumnAttribute> atributu Určete vlastnost nebo pole představující primární klíč pro sloupec databáze. <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b0da-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a property or field to represent the primary key for a database column.</span></span>  
  
 <span data-ttu-id="0b0da-104">Příklady kódu naleznete v tématu <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="0b0da-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span></span>  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="0b0da-105">nepodporuje počítané sloupce jako primární klíče.</span><span class="sxs-lookup"><span data-stu-id="0b0da-105">does not support computed columns as primary keys.</span></span>  
  
### <a name="to-designate-a-property-or-field-as-a-primary-key"></a><span data-ttu-id="0b0da-106">Určení vlastnosti nebo pole jako primárního klíče</span><span class="sxs-lookup"><span data-stu-id="0b0da-106">To designate a property or field as a primary key</span></span>  
  
1. <span data-ttu-id="0b0da-107"><xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> Přidejte vlastnost<xref:System.Data.Linq.Mapping.ColumnAttribute> do atributu.</span><span class="sxs-lookup"><span data-stu-id="0b0da-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="0b0da-108">Zadejte hodnotu jako `true`.</span><span class="sxs-lookup"><span data-stu-id="0b0da-108">Specify the value as `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b0da-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0b0da-109">See also</span></span>

- [<span data-ttu-id="0b0da-110">Objektový model LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="0b0da-110">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="0b0da-111">Postupy: Přizpůsobení tříd entit pomocí editoru kódu</span><span class="sxs-lookup"><span data-stu-id="0b0da-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
