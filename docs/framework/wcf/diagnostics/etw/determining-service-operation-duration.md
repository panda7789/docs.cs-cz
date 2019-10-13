---
title: Určení doby trvání operace služby
ms.date: 03/30/2017
ms.assetid: e8a93a2c-2c20-48b3-8986-57e90e9aa908
ms.openlocfilehash: 06a4c2da7b702fa4fbc1469576c118b790803339
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291421"
---
# <a name="determining-service-operation-duration"></a>Určení doby trvání operace služby
Pokud je v aplikaci Windows Communication Foundation (WCF) povolené analytické trasování, můžete dobu trvání provádění operace služby snadno určit kontrolou protokolu událostí.  Toto téma ukazuje, jak určit, jak dlouho trvá operace služby.  
  
### <a name="determining-service-operation-execution-duration"></a>Určení doby trvání provádění operace služby  
  
1. Otevřete Prohlížeč událostí kliknutím na tlačítko **Start**, **Spustit**a zadáním `eventvwr.exe`.  
  
2. Pokud jste nepovolili analytické trasování, rozbalte **protokoly aplikací a služeb**, **Microsoft**, **Windows**, **aplikační server – aplikace**. Vyberte **zobrazení**, **Zobrazte protokoly o ladění a ladění**. Klikněte pravým tlačítkem na možnost **analytické** a vyberte **Povolit protokol**. Nechejte Prohlížeč událostí otevřené, aby trasování bylo možné zobrazit po spuštění operace služby.  
  
3. Dále otevřete aplikaci WCF, která obsahuje projekt služby a klientský projekt, který komunikuje s touto službou.  Takovou aplikaci můžete vytvořit pomocí [Začínáme kurzu](../../getting-started-tutorial.md).  Pokud máte nainstalované ukázky WCF, můžete otevřít [Začínáme](../../samples/getting-started-sample.md), který obsahuje dokončený projekt vytvořený v tomto kurzu.  
  
4. Spusťte serverovou aplikaci stisknutím klávesy **F5**. Spusťte klientskou aplikaci tak, že kliknete pravým tlačítkem na projekt **klienta** a vyberete **ladění**, **zahájíte novou instanci**.  
  
5. V Prohlížeč událostí aktualizujte analytický protokol a seřaďte události podle ID události.  Vyhledejte události s ID události [214-volána OperationCompleted](214-operationcompleted.md).  Tyto události zobrazí informace o dokončených operacích a o době trvání operace.  Následující událost ukazuje dobu trvání operace přidání.  
  
    ```output  
    An OperationInvoker completed the call to the 'Add' method.  The method call duration was '3' ms.  
    ```
