---
title: Zjišťování doby provádění operací služby
ms.date: 03/30/2017
ms.assetid: e8a93a2c-2c20-48b3-8986-57e90e9aa908
ms.openlocfilehash: 9bc38f40b22eca8278905440ee69af9f38b81a0d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798109"
---
# <a name="determining-service-operation-duration"></a>Zjišťování doby provádění operací služby
Pokud je v aplikaci Windows Communication Foundation (WCF) povolené analytické trasování, můžete dobu trvání provádění operace služby snadno určit kontrolou protokolu událostí.  Toto téma ukazuje, jak určit, jak dlouho trvá operace služby.  
  
### <a name="determining-service-operation-execution-duration"></a>Určení doby trvání provádění operace služby  
  
1. Otevřete Prohlížeč událostí kliknutím na **Start**, **Spustit**a zadáním `eventvwr.exe`.  
  
2. Pokud jste nepovolili analytické trasování, rozbalte **protokoly aplikací a služeb**, **Microsoft**, **Windows**, **aplikační server – aplikace**. Vyberte **zobrazení**, **Zobrazte protokoly o ladění a ladění**. Klikněte pravým tlačítkem na možnost **analytické** a vyberte **Povolit protokol**. Nechejte Prohlížeč událostí otevřené, aby trasování bylo možné zobrazit po spuštění operace služby.  
  
3. Dále otevřete aplikaci WCF, která obsahuje projekt služby a klientský projekt, který komunikuje s touto službou.  Takovou aplikaci můžete vytvořit pomocí [Začínáme kurzu](../../getting-started-tutorial.md).  Pokud máte nainstalované ukázky WCF, můžete otevřít [Začínáme](../../samples/getting-started-sample.md), který obsahuje dokončený projekt vytvořený v tomto kurzu.  
  
4. Spusťte serverovou aplikaci stisknutím klávesy **F5**. Spusťte klientskou aplikaci tak, že kliknete pravým tlačítkem na projekt **klienta** a vyberete **ladění**, **zahájíte novou instanci**.  
  
5. V Prohlížeč událostí aktualizujte analytický protokol a seřaďte události podle ID události.  Vyhledejte události s ID události [214-volána OperationCompleted](214-operationcompleted.md).  Tyto události zobrazí informace o dokončených operacích a o době trvání operace.  Následující událost ukazuje dobu trvání operace přidání.  
  
    ```Output  
    An OperationInvoker completed the call to the 'Add' method.  The method call duration was '3' ms.  
    ```
