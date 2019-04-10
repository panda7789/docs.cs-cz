---
title: Možnost kódování instance
ms.date: 03/30/2017
ms.assetid: 89e4b029-4f68-438c-8117-9b21fe094ef4
ms.openlocfilehash: c4de7c45d899f45a7b5b71d563257d9accb8fdbb
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59315618"
---
# <a name="instance-encoding-option"></a><span data-ttu-id="16e9f-102">Možnost kódování instance</span><span class="sxs-lookup"><span data-stu-id="16e9f-102">Instance Encoding Option</span></span>
<span data-ttu-id="16e9f-103">**Možnost kódování Instance** vlastnost Store Instance pracovního postupu SQL umožňuje určit, zda by měl poskytovatele trvalosti SQL komprimovat informace stavu instance pracovního postupu pomocí algoritmu GZip před uložením informace do databáze trvalosti.</span><span class="sxs-lookup"><span data-stu-id="16e9f-103">The **Instance Encoding Option** property of the SQL Workflow Instance Store lets you specify whether the SQL persistence provider should compress the workflow instance state information using the GZip algorithm before saving the information into the persistence database.</span></span> <span data-ttu-id="16e9f-104">Povolené hodnoty této vlastnosti jsou: GZip a None.</span><span class="sxs-lookup"><span data-stu-id="16e9f-104">The allowed values for this property are: GZip and None.</span></span> <span data-ttu-id="16e9f-105">Výchozí hodnota je žádné.</span><span class="sxs-lookup"><span data-stu-id="16e9f-105">The default value is None.</span></span> <span data-ttu-id="16e9f-106">Následující seznam popisuje tyto možnosti.</span><span class="sxs-lookup"><span data-stu-id="16e9f-106">The following list describes these options.</span></span>  
  
1. <span data-ttu-id="16e9f-107">**GZip**.</span><span class="sxs-lookup"><span data-stu-id="16e9f-107">**GZip**.</span></span> <span data-ttu-id="16e9f-108">Poskytovatel trvalého kóduje informace o stavu pomocí algoritmu GZip před uložením informace o stavu databáze trvalosti.</span><span class="sxs-lookup"><span data-stu-id="16e9f-108">The persistence provider encodes the state information using the GZip algorithm before persisting the state information in the persistence database.</span></span>  
  
2. <span data-ttu-id="16e9f-109">**Žádný**.</span><span class="sxs-lookup"><span data-stu-id="16e9f-109">**None**.</span></span> <span data-ttu-id="16e9f-110">Poskytovatel trvalého neprovádí kódování informace o stavu před uložením informace do databáze trvalosti.</span><span class="sxs-lookup"><span data-stu-id="16e9f-110">The persistence provider does not encode the state information before saving the information into the persistence database.</span></span>  
  
 <span data-ttu-id="16e9f-111">Kódování instance informace o stavu pracovního postupu pomocí GZip snižuje spotřebu paměti ve službě SQL database a také snižuje využití sítě, pokud se databáze nachází na jiný počítač v síti z počítače, na kterém je hostitel služby pracovního postupu spuštění.</span><span class="sxs-lookup"><span data-stu-id="16e9f-111">Encoding workflow instance state information using the GZip reduces memory consumption in the SQL database and also reduces network consumption if the database resides on a different computer on the network from the computer on which the workflow service host is running.</span></span> <span data-ttu-id="16e9f-112">Obecné pokyny, je nastavit **možnost kódování Instance** vlastnost **žádný** Pokud stav instance pracovního postupu je nízká.</span><span class="sxs-lookup"><span data-stu-id="16e9f-112">A general guidance is to set the **Instance Encoding Option** property to **None** if the workflow instance state is small.</span></span>
