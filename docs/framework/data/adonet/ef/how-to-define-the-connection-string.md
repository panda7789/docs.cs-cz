---
title: 'Postupy: Definování připojovacího řetězce'
ms.date: 03/30/2017
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
ms.openlocfilehash: f40b8bc68eda1cb4b64b34d12b2922da69929203
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43802158"
---
# <a name="how-to-define-the-connection-string"></a>Postupy: Definování připojovacího řetězce
Toto téma ukazuje, jak definovat připojovací řetězec, který je použit při připojování ke konceptuálního modelu. Toto téma vychází [AdventureWorks prodeje](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) koncepčního modelu. AdventureWorks Sales Model se používá v tématech souvisejících s úlohami v rámci [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] dokumentaci. Toto téma předpokládá, že jste již nakonfigurovali [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] a definovaný Model prodeje AdventureWorks. Další informace najdete v tématu [postupy: ruční definování modelu a souborů mapování](https://msdn.microsoft.com/library/d4fd6864-f2a1-48f0-aa32-1e318775a99a). Postupy v tomto tématu jsou taky součástí [postupy: ruční konfigurace projektu v Entity Framework](https://msdn.microsoft.com/library/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e).  
  
> [!NOTE]
>  Pokud používáte [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] průvodce v projektu sady Visual Studio automaticky vygeneruje soubor .edmx a nakonfiguruje projekt na používání [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Další informace najdete v tématu [postupy: použití Průvodce datovým modelem Entity](https://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d)  
  
### <a name="to-define-the-entity-framework-connection-string"></a>K definování připojovacího řetězce Entity Framework  
  
-   Otevřete konfigurační soubor projektu aplikace (app.config) a přidejte následující připojovací řetězec:  
  
  
  
     Pokud váš projekt nemá konfiguračního souboru aplikace, můžete výběrem možnosti Přidat **přidat novou položku** z **projektu** nabídce vyberete **Obecné** kategorie, Výběr **konfiguračního souboru aplikace**a pak levým na **přidat**.  
  
## <a name="see-also"></a>Viz také  
 [Rychlý start](https://msdn.microsoft.com/library/0bc534be-789f-4819-b9f6-76e51d961675)  
 [Postupy: vytvoření nového souboru EDMX](https://msdn.microsoft.com/library/beb8189e-e51c-4051-839c-9902c224abf2)  
 [Datový Model Entity ADO.NET nástroje](https://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527)
