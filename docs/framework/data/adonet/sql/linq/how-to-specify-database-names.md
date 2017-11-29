---
title: "Postupy: Zadejte názvy databází"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b80f0fd2-7f75-45fe-9e12-496f80f183df
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 998a720f4e2cd7c3a63578d1025d0dd7b42a1b92
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-database-names"></a><span data-ttu-id="024e1-102">Postupy: Zadejte názvy databází</span><span class="sxs-lookup"><span data-stu-id="024e1-102">How to: Specify Database Names</span></span>
<span data-ttu-id="024e1-103">Použití <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> vlastnost <xref:System.Data.Linq.Mapping.DatabaseAttribute> atribut určit název databáze, když není zadaný název připojení.</span><span class="sxs-lookup"><span data-stu-id="024e1-103">Use the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property on a <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute to specify the name of a database when a name is not supplied by the connection.</span></span>  
  
 <span data-ttu-id="024e1-104">Ukázky kódu, najdete v části <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span><span class="sxs-lookup"><span data-stu-id="024e1-104">For code samples, see <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span></span>  
  
### <a name="to-specify-the-name-of-the-database"></a><span data-ttu-id="024e1-105">Zadat název databáze</span><span class="sxs-lookup"><span data-stu-id="024e1-105">To specify the name of the database</span></span>  
  
1.  <span data-ttu-id="024e1-106">Přidat <xref:System.Data.Linq.Mapping.DatabaseAttribute> atribut deklarace třídy pro databázi.</span><span class="sxs-lookup"><span data-stu-id="024e1-106">Add the <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute to the class declaration for the database.</span></span>  
  
2.  <span data-ttu-id="024e1-107">Přidat <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> vlastnost, která má <xref:System.Data.Linq.Mapping.DatabaseAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="024e1-107">Add the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property to the <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute.</span></span>  
  
3.  <span data-ttu-id="024e1-108">Nastavte <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> hodnotu vlastnosti na název, který chcete zadat.</span><span class="sxs-lookup"><span data-stu-id="024e1-108">Set the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property value to the name that you want to specify.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="024e1-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="024e1-109">See Also</span></span>  
 [<span data-ttu-id="024e1-110">Technologie LINQ to SQL objektový Model</span><span class="sxs-lookup"><span data-stu-id="024e1-110">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="024e1-111">Postupy: přizpůsobení tříd entit pomocí editoru kódu</span><span class="sxs-lookup"><span data-stu-id="024e1-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
