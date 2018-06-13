---
title: Kódování možnost instance
ms.date: 03/30/2017
ms.assetid: 89e4b029-4f68-438c-8117-9b21fe094ef4
ms.openlocfilehash: cfe45428f546b6f47709c321099efdf7fbb25ef4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33512535"
---
# <a name="instance-encoding-option"></a><span data-ttu-id="dfd02-102">Kódování možnost instance</span><span class="sxs-lookup"><span data-stu-id="dfd02-102">Instance Encoding Option</span></span>
<span data-ttu-id="dfd02-103">**Instance kódování možnost** vlastnost úložiště Instance pracovního postupu SQL umožňuje určit, zda zprostředkovatel trvalost SQL by měl komprimovat informace stavu instance pracovního postupu pomocí algoritmu GZip před uložením informace do databáze trvalost.</span><span class="sxs-lookup"><span data-stu-id="dfd02-103">The **Instance Encoding Option** property of the SQL Workflow Instance Store lets you specify whether the SQL persistence provider should compress the workflow instance state information using the GZip algorithm before saving the information into the persistence database.</span></span> <span data-ttu-id="dfd02-104">Povolené hodnoty pro tuto vlastnost jsou: GZip a None.</span><span class="sxs-lookup"><span data-stu-id="dfd02-104">The allowed values for this property are: GZip and None.</span></span> <span data-ttu-id="dfd02-105">Výchozí hodnota je žádné.</span><span class="sxs-lookup"><span data-stu-id="dfd02-105">The default value is None.</span></span> <span data-ttu-id="dfd02-106">Následující seznam popisuje tyto možnosti.</span><span class="sxs-lookup"><span data-stu-id="dfd02-106">The following list describes these options.</span></span>  
  
1.  <span data-ttu-id="dfd02-107">**GZip**.</span><span class="sxs-lookup"><span data-stu-id="dfd02-107">**GZip**.</span></span> <span data-ttu-id="dfd02-108">Zprostředkovatel trvalost kóduje informace o stavu pomocí algoritmu GZip před uložením informace o stavu v databázi trvalost.</span><span class="sxs-lookup"><span data-stu-id="dfd02-108">The persistence provider encodes the state information using the GZip algorithm before persisting the state information in the persistence database.</span></span>  
  
2.  <span data-ttu-id="dfd02-109">**Žádný**.</span><span class="sxs-lookup"><span data-stu-id="dfd02-109">**None**.</span></span> <span data-ttu-id="dfd02-110">Zprostředkovatel trvalost neprovádí kódování informace o stavu před uložením informace do databáze trvalost.</span><span class="sxs-lookup"><span data-stu-id="dfd02-110">The persistence provider does not encode the state information before saving the information into the persistence database.</span></span>  
  
 <span data-ttu-id="dfd02-111">Kódování instance informace o stavu pracovního postupu pomocí GZip snižuje využití paměti v databázi SQL a také snižuje spotřeba síťových, pokud se databáze nachází v jiném počítači v síti z počítače, na která hostitele služby pracovního postupu spuštěna.</span><span class="sxs-lookup"><span data-stu-id="dfd02-111">Encoding workflow instance state information using the GZip reduces memory consumption in the SQL database and also reduces network consumption if the database resides on a different computer on the network from the computer on which the workflow service host is running.</span></span> <span data-ttu-id="dfd02-112">Obecné pokyny je nastavit **Instance kódování možnost** vlastnost **žádné** Pokud stav instance pracovního postupu je malá.</span><span class="sxs-lookup"><span data-stu-id="dfd02-112">A general guidance is to set the **Instance Encoding Option** property to **None** if the workflow instance state is small.</span></span>
