---
title: 'Postupy: Zadání názvů databází'
ms.date: 03/30/2017
ms.assetid: b80f0fd2-7f75-45fe-9e12-496f80f183df
ms.openlocfilehash: 0daf754edf624410e0ea725acd6c266ccb7828dc
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781573"
---
# <a name="how-to-specify-database-names"></a><span data-ttu-id="ebd58-102">Postupy: Zadání názvů databází</span><span class="sxs-lookup"><span data-stu-id="ebd58-102">How to: Specify Database Names</span></span>
<span data-ttu-id="ebd58-103"><xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> Pomocí vlastnosti<xref:System.Data.Linq.Mapping.DatabaseAttribute> u atributu určete název databáze, pokud není název dodán připojením.</span><span class="sxs-lookup"><span data-stu-id="ebd58-103">Use the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property on a <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute to specify the name of a database when a name is not supplied by the connection.</span></span>  
  
 <span data-ttu-id="ebd58-104">Ukázky kódu naleznete v tématu <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span><span class="sxs-lookup"><span data-stu-id="ebd58-104">For code samples, see <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span></span>  
  
### <a name="to-specify-the-name-of-the-database"></a><span data-ttu-id="ebd58-105">Určení názvu databáze</span><span class="sxs-lookup"><span data-stu-id="ebd58-105">To specify the name of the database</span></span>  
  
1. <span data-ttu-id="ebd58-106"><xref:System.Data.Linq.Mapping.DatabaseAttribute> Přidejte atribut do deklarace třídy pro databázi.</span><span class="sxs-lookup"><span data-stu-id="ebd58-106">Add the <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute to the class declaration for the database.</span></span>  
  
2. <span data-ttu-id="ebd58-107"><xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> Přidejte vlastnost<xref:System.Data.Linq.Mapping.DatabaseAttribute> do atributu.</span><span class="sxs-lookup"><span data-stu-id="ebd58-107">Add the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property to the <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute.</span></span>  
  
3. <span data-ttu-id="ebd58-108">Nastavte hodnotu <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> vlastnosti na název, který chcete zadat.</span><span class="sxs-lookup"><span data-stu-id="ebd58-108">Set the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property value to the name that you want to specify.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebd58-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ebd58-109">See also</span></span>

- [<span data-ttu-id="ebd58-110">Objektový model LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="ebd58-110">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="ebd58-111">Postupy: Přizpůsobení tříd entit pomocí editoru kódu</span><span class="sxs-lookup"><span data-stu-id="ebd58-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
