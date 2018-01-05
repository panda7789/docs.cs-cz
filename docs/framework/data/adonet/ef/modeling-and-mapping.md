---
title: "Mapování a modelování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ec8a9515-3708-4cde-a688-4d8e6975f150
caps.latest.revision: "7"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: a219e4e3a58e3bd3e71bab3d3c41c87c393b20da
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="modeling-and-mapping"></a>Mapování a modelování
V [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], můžete definovat Koncepční model, modelu úložiště a mapování mezi těmito dvěma způsobem, který nejlépe vyhovuje vaší aplikace. Nástroje Entity Data Model v [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] vám umožňují vytvořit.[ soubor EDMX](http://msdn.microsoft.com/en-us/f4c8e7ce-1db6-417e-9759-15f8b55155d4) z databáze nebo grafické modelu a poté aktualizace které souboru při změně databáze nebo model.  
  
 Od verze Entity Framework 4.1 můžete také vytvořit model programově pomocí Code First vývoj. Existují dva různé scénáře pro vývoj Code First. V obou případech vývojář definuje model pomocí kódování definice tříd rozhraní .NET Framework a poté Volitelně můžete určit další mapování nebo konfigurace pomocí datových poznámek nebo rozhraní fluent API.  
  
 Další informace najdete v tématu [vytvoření a mapování konceptuálního modelu](http://go.microsoft.com/fwlink/?LinkId=235016).  
  
 Můžete také použít Generátor EDM, který je součástí [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)]. EdmGen.exe generuje .csdl, .ssdl a .msl soubory z existujícího zdroje dat. Můžete také ručně vytvořit model a mapování obsahu. Další informace najdete v tématu [EDM generátor (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md).
