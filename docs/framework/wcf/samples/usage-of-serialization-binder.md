---
title: "Použití vazače serializace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ab46c087-200c-45bf-9c95-5a6cda6e8b98
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 77f5c2914051c4310102a57b7181333bab6811b6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="usage-of-serialization-binder"></a>Použití vazače serializace
Tento příklad ukazuje způsob použití <xref:System.Runtime.Serialization.SerializationBinder> změna verze obecného typu, pokud je serializováno.  
  
## <a name="demonstrates"></a>Demonstruje  
 <xref:System.Runtime.Serialization.SerializationBinder>, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>  
  
## <a name="discussion"></a>Diskusní  
 Tento příklad ukazuje, jak dvě entity, které jsou cílené na různých verzích [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] může komunikovat pomocí binární formátovacího modulu a vazače serializace.  
  
 Vývoj této ukázky bylo provedeno pomocí .NET Remoting. Ukázkový soubor obsahuje cílení na serverový [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)], který implementuje kontrakt s obecné typy a dvou různých klientů, jeden cílení na [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)] a jiné cílení [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)].  
  
 Připojí serveru <xref:System.Runtime.Serialization.SerializationBinder> na binární formátování, které bude moci změnit verzi typy odpovídajícím způsobem v serializaci, tak i klientů může deserializovat tyto typy správně.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Spuštění klienta, klikněte pravým tlačítkem na řešení, SBGenericsVTS (6 projektů) a potom vyberte **vlastnosti**.  
  
2.  V **společných vlastností**, vyberte **spouštěný projekt**, pak vyberte **více projektů po spuštění**.  
  
3.  Vyberte **Server** první, pak **Client20** a potom **Client40**. Vyberte **spustit** akce do těchto tří projektů a ponechejte zbývající nastavena na **žádné**.  
  
4.  Klikněte na tlačítko **OK** a potom stiskněte klávesu F5 a spusťte vzorku.
