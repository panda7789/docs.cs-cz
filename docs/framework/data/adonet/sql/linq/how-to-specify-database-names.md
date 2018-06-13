---
title: 'Postupy: Zadejte názvy databází'
ms.date: 03/30/2017
ms.assetid: b80f0fd2-7f75-45fe-9e12-496f80f183df
ms.openlocfilehash: a69fa1723c0660d3c6dfa8bfa7ec3b9e4dc75d7c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33361582"
---
# <a name="how-to-specify-database-names"></a><span data-ttu-id="98a66-102">Postupy: Zadejte názvy databází</span><span class="sxs-lookup"><span data-stu-id="98a66-102">How to: Specify Database Names</span></span>
<span data-ttu-id="98a66-103">Použití <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> vlastnost <xref:System.Data.Linq.Mapping.DatabaseAttribute> atribut určit název databáze, když není zadaný název připojení.</span><span class="sxs-lookup"><span data-stu-id="98a66-103">Use the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property on a <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute to specify the name of a database when a name is not supplied by the connection.</span></span>  
  
 <span data-ttu-id="98a66-104">Ukázky kódu, najdete v části <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span><span class="sxs-lookup"><span data-stu-id="98a66-104">For code samples, see <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span></span>  
  
### <a name="to-specify-the-name-of-the-database"></a><span data-ttu-id="98a66-105">Zadat název databáze</span><span class="sxs-lookup"><span data-stu-id="98a66-105">To specify the name of the database</span></span>  
  
1.  <span data-ttu-id="98a66-106">Přidat <xref:System.Data.Linq.Mapping.DatabaseAttribute> atribut deklarace třídy pro databázi.</span><span class="sxs-lookup"><span data-stu-id="98a66-106">Add the <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute to the class declaration for the database.</span></span>  
  
2.  <span data-ttu-id="98a66-107">Přidat <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> vlastnost, která má <xref:System.Data.Linq.Mapping.DatabaseAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="98a66-107">Add the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property to the <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute.</span></span>  
  
3.  <span data-ttu-id="98a66-108">Nastavte <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> hodnotu vlastnosti na název, který chcete zadat.</span><span class="sxs-lookup"><span data-stu-id="98a66-108">Set the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property value to the name that you want to specify.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98a66-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="98a66-109">See Also</span></span>  
 [<span data-ttu-id="98a66-110">Objektový model LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="98a66-110">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="98a66-111">Postupy: Přizpůsobení tříd entit pomocí editoru kódu</span><span class="sxs-lookup"><span data-stu-id="98a66-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
