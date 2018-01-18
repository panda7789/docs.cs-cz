---
title: "Postupy: definování připojovací řetězec"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c7c17029dade53c724420fa5604ba3448ce6a6ab
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-define-the-connection-string"></a>Postupy: definování připojovací řetězec
Toto téma ukazuje, jak zadat připojovací řetězec, který se používá při připojování k konceptuálního modelu. Toto téma je založena na [AdventureWorks prodej](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) konceptuálního modelu. Model organizační jednotky prodej AdventureWorks se používá v rámci úlohy související témata v [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] dokumentaci. Toto téma předpokládá, že jste již nakonfigurovali [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] a definované Model prodeje společnosti AdventureWorks. Další informace najdete v tématu [postupy: ruční definování modelu a mapování souborů](http://msdn.microsoft.com/en-us/d4fd6864-f2a1-48f0-aa32-1e318775a99a). Postupy v tomto tématu jsou také obsaženy v [postupy: ruční konfigurace projektu Entity Framework](http://msdn.microsoft.com/en-us/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e).  
  
> [!NOTE]
>  Pokud použijete [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] průvodce v nástroji [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] projektu, automaticky vygeneruje soubor EDMX a nakonfiguruje projektu pro použití [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Další informace najdete v tématu [postupy: použití průvodce Entity Data Model](http://msdn.microsoft.com/en-us/dadb058a-c5d9-4c5c-8b01-28044112231d)  
  
### <a name="to-define-the-entity-framework-connection-string"></a>Chcete-li definovat připojovací řetězec Entity Framework  
  
-   Otevřete konfigurační soubor projektu aplikace (app.config) a přidejte následující připojovací řetězec:  
  
  
  
     Pokud projekt nemá konfiguračního souboru aplikace, můžete přidat výběrem možnosti **přidat novou položku** z **projektu** nabídce vyberete **Obecné** kategorie, Výběr **konfigurační soubor aplikace**a pak levým na **přidat**.  
  
## <a name="see-also"></a>Viz také  
 [Rychlý start](http://msdn.microsoft.com/en-us/0bc534be-789f-4819-b9f6-76e51d961675)  
 [Postupy: vytvoření nového souboru EDMX](http://msdn.microsoft.com/en-us/beb8189e-e51c-4051-839c-9902c224abf2)  
 [Nástroje modelu ADO.NET Entity Data Model](http://msdn.microsoft.com/en-us/91076853-0881-421b-837a-f582f36be527)
