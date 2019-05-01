---
title: 'Postupy: Zadání názvů databází'
ms.date: 03/30/2017
ms.assetid: b80f0fd2-7f75-45fe-9e12-496f80f183df
ms.openlocfilehash: a43a7ac541adb984eeb8bb88b7ab96db86baf26c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62037567"
---
# <a name="how-to-specify-database-names"></a><span data-ttu-id="5a6c8-102">Postupy: Zadání názvů databází</span><span class="sxs-lookup"><span data-stu-id="5a6c8-102">How to: Specify Database Names</span></span>
<span data-ttu-id="5a6c8-103">Použití <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> vlastnosti <xref:System.Data.Linq.Mapping.DatabaseAttribute> atribut k zadání názvu databáze, pokud není zadán název připojení.</span><span class="sxs-lookup"><span data-stu-id="5a6c8-103">Use the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property on a <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute to specify the name of a database when a name is not supplied by the connection.</span></span>  
  
 <span data-ttu-id="5a6c8-104">Ukázky kódu najdete v tématu <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span><span class="sxs-lookup"><span data-stu-id="5a6c8-104">For code samples, see <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span></span>  
  
### <a name="to-specify-the-name-of-the-database"></a><span data-ttu-id="5a6c8-105">Chcete-li určit název databáze</span><span class="sxs-lookup"><span data-stu-id="5a6c8-105">To specify the name of the database</span></span>  
  
1. <span data-ttu-id="5a6c8-106">Přidat <xref:System.Data.Linq.Mapping.DatabaseAttribute> atribut deklarace třídy pro databázi.</span><span class="sxs-lookup"><span data-stu-id="5a6c8-106">Add the <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute to the class declaration for the database.</span></span>  
  
2. <span data-ttu-id="5a6c8-107">Přidat <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> vlastnost <xref:System.Data.Linq.Mapping.DatabaseAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="5a6c8-107">Add the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property to the <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute.</span></span>  
  
3. <span data-ttu-id="5a6c8-108">Nastavte <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> hodnotu vlastnosti na název, který chcete zadat.</span><span class="sxs-lookup"><span data-stu-id="5a6c8-108">Set the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property value to the name that you want to specify.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a6c8-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5a6c8-109">See also</span></span>

- [<span data-ttu-id="5a6c8-110">Objektový model LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="5a6c8-110">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="5a6c8-111">Postupy: Přizpůsobení tříd entit pomocí editoru kódu</span><span class="sxs-lookup"><span data-stu-id="5a6c8-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
