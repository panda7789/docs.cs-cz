---
title: Mapování a modelování
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec8a9515-3708-4cde-a688-4d8e6975f150
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: e7bd382cf2183bcd84c7ad4a420dcbd7570e0685
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="modeling-and-mapping"></a><span data-ttu-id="2824d-102">Mapování a modelování</span><span class="sxs-lookup"><span data-stu-id="2824d-102">Modeling and Mapping</span></span>
<span data-ttu-id="2824d-103">V [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], můžete definovat Koncepční model, modelu úložiště a mapování mezi těmito dvěma způsobem, který nejlépe vyhovuje vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="2824d-103">In the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], you can define the conceptual model, storage model, and the mapping between the two in the way that best suits your application.</span></span> <span data-ttu-id="2824d-104">Nástroje modelu Entity Data v sadě Visual Studio umožňují vytvářet. [souboru edmx](http://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4) z databáze nebo grafické modelu a poté aktualizace které souboru při změně databáze nebo model.</span><span class="sxs-lookup"><span data-stu-id="2824d-104">The Entity Data Model Tools in Visual Studio allow you to create an .[edmx file](http://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4) from a database or a graphical model and then update that file when either the database or model changes.</span></span>  
  
 <span data-ttu-id="2824d-105">Od verze Entity Framework 4.1 můžete také vytvořit model programově pomocí Code First vývoj.</span><span class="sxs-lookup"><span data-stu-id="2824d-105">Starting with the Entity Framework 4.1 you can also create a model programmatically using Code First development.</span></span> <span data-ttu-id="2824d-106">Existují dva různé scénáře pro vývoj Code First.</span><span class="sxs-lookup"><span data-stu-id="2824d-106">There are two different scenarios for Code First development.</span></span> <span data-ttu-id="2824d-107">V obou případech vývojář definuje model pomocí kódování definice tříd rozhraní .NET Framework a poté Volitelně můžete určit další mapování nebo konfigurace pomocí datových poznámek nebo rozhraní fluent API.</span><span class="sxs-lookup"><span data-stu-id="2824d-107">In both cases, the developer defines a model by coding .NET Framework class definitions, and then optionally specifies additional mapping or configuration by using Data Annotations or the fluent API.</span></span>  
  
 <span data-ttu-id="2824d-108">Další informace najdete v tématu [vytvoření a mapování konceptuálního modelu](http://go.microsoft.com/fwlink/?LinkId=235016).</span><span class="sxs-lookup"><span data-stu-id="2824d-108">For more information, see [Creating and Mapping a Conceptual Model](http://go.microsoft.com/fwlink/?LinkId=235016).</span></span>  
  
 <span data-ttu-id="2824d-109">Můžete také použít Generátor EDM, který je součástí [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2824d-109">You can also use the EDM Generator, which is included with the [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="2824d-110">EdmGen.exe generuje .csdl, .ssdl a .msl soubory z existujícího zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="2824d-110">The EdmGen.exe generates the .csdl, .ssdl, and .msl files from an existing data source.</span></span> <span data-ttu-id="2824d-111">Můžete také ručně vytvořit model a mapování obsahu.</span><span class="sxs-lookup"><span data-stu-id="2824d-111">You can also manually create the model and mapping content.</span></span> <span data-ttu-id="2824d-112">Další informace najdete v tématu [EDM generátor (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md).</span><span class="sxs-lookup"><span data-stu-id="2824d-112">For more information, see [EDM Generator (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md).</span></span>
