---
title: "Zjišťování doby provádění operací služby"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8a93a2c-2c20-48b3-8986-57e90e9aa908
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 63a8c92713ee452da2439475ac526229d1e5741c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="determining-service-operation-duration"></a>Zjišťování doby provádění operací služby
Pokud je povoleno analytické trasování v [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] aplikace, doba provádění pro operaci služby se dá snadno určit pomocí protokolu událostí.  Toto téma ukazuje, jak určit množství času, které operace služby potřebné k dokončení.  
  
### <a name="determining-service-operation-execution-duration"></a>Určení doba trvání provádění operace služby  
  
1.  Otevřete Prohlížeč událostí kliknutím **spustit**, **spustit**a zadáním `eventvwr.exe`.  
  
2.  Pokud jste nepovolili analytické trasování, rozbalte položku **protokoly aplikací a služeb**, **Microsoft**, **Windows**, **serveru aplikace – aplikace** . Vyberte **zobrazení**, **ukazují analytické a ladicí protokoly**. Klikněte pravým tlačítkem na **analytické** a vyberte **povolit protokol**. Ponechte prohlížeče událostí otevřete tak, aby trasování lze zobrazit po spuštění operace služby.  
  
3.  Dále otevřete [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] aplikace, která zahrnuje službu projekt a projekt klienta, který komunikuje s touto službou.  Takové aplikace můžete vytvořit pomocí následujících [kurzu Začínáme](../../../../../docs/framework/wcf/getting-started-tutorial.md).  Pokud máte [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] ukázky nainstalován, můžete otevřít [Začínáme](../../../../../docs/framework/wcf/samples/getting-started-sample.md), obsahující dokončený projekt vytvořený v tomto kurzu.  
  
4.  Spusťte aplikaci server tak, že stisknete **F5**. Spusťte klientská aplikace tak, že pravým tlačítkem myši na **klienta** projekt a výběrem **ladění**, **spustit novou instanci**.  
  
5.  V prohlížeči událostí aktualizujte protokol analytické a seřaďte události podle ID události.  Vyhledejte události s ID události [214 – metoda OperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/214-operationcompleted.md).  Tyto události se zobrazí operací, které byly dokončeny, a jak se doba trvání operace.  Následující událost zobrazuje dobu trvání operace přidat.  
  
    ```Output  
    An OperationInvoker completed the call to the 'Add' method.  The method call duration was '3' ms.  
    ```
