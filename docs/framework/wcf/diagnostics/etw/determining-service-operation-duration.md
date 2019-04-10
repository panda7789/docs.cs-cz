---
title: Zjišťování doby provádění operací služby
ms.date: 03/30/2017
ms.assetid: e8a93a2c-2c20-48b3-8986-57e90e9aa908
ms.openlocfilehash: fd7dec5784f50a0613b574822a31202a859b34c6
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59299030"
---
# <a name="determining-service-operation-duration"></a>Zjišťování doby provádění operací služby
Pokud analytické trasování je povolené v aplikaci Windows Communication Foundation (WCF), doba trvání spuštění pro operaci služby můžete snadno určit, naleznete v protokolu událostí.  Toto téma ukazuje, jak určit množství času, které zabere operaci služby.  
  
### <a name="determining-service-operation-execution-duration"></a>Zjišťování doby provádění provádění operací služby  
  
1. Otevřete Prohlížeč událostí kliknutím **Start**, **spustit**a zadat `eventvwr.exe`.  
  
2. Pokud jste ještě nepovolili analytické trasování, rozbalte **protokoly aplikací a služeb**, **Microsoft**, **Windows**, **serveru aplikace** . Vyberte **zobrazení**, **zobrazit analytické a ladit protokoly**. Klikněte pravým tlačítkem na **analytické** a vyberte **povolit protokol**. Prohlížeč událostí ponechte otevřené, aby trasování můžete zobrazit po provedení operace služby.  
  
3. Dále otevřete aplikaci WCF, která obsahuje projekt služby a klientský projekt, který komunikuje s touto službou.  Můžete vytvořit takovou aplikaci pomocí následujících [kurz Začínáme](../../../../../docs/framework/wcf/getting-started-tutorial.md).  Pokud máte nainstalované Ukázky WCF, můžete otevřít [Začínáme](../../../../../docs/framework/wcf/samples/getting-started-sample.md), který obsahuje dokončený projekt vytvořený v tomto kurzu.  
  
4. Spusťte serverovou aplikaci stisknutím klávesy **F5**. Kliknutím pravým tlačítkem na spuštění klientské aplikace **klienta** projekt a výběrem **ladění**, **spustit novou instanci**.  
  
5. V prohlížeči událostí aktualizujte v analytickém protokolu a seřaďte události podle ID události.  Hledejte události s ID události [214 – metoda OperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/214-operationcompleted.md).  Tyto události se zobrazí dokončení operace, které a jak se doba trvání operace.  Následující událost zobrazuje dobu trvání operace přidat.  
  
    ```Output  
    An OperationInvoker completed the call to the 'Add' method.  The method call duration was '3' ms.  
    ```
