---
title: Použití vazače serializace
ms.date: 03/30/2017
ms.assetid: ab46c087-200c-45bf-9c95-5a6cda6e8b98
ms.openlocfilehash: bfce2a14c8757250c520919c8ff2a4d7048a9d5c
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2019
ms.locfileid: "74138645"
---
# <a name="usage-of-serialization-binder"></a>Použití vazače serializace
Tento příklad ukazuje, jak použít <xref:System.Runtime.Serialization.SerializationBinder> ke změně verze obecného typu při jeho serializaci.  
  
## <a name="demonstrates"></a>Demonstruje  
 <xref:System.Runtime.Serialization.SerializationBinder><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>  
  
## <a name="discussion"></a>Účely  
 Tento příklad ukazuje, jak mohou dvě entity, které cílí na různé verze .NET Framework, komunikovat pomocí binárního formátovacího modulu a pořadače serializace.  
  
Tato ukázka byla vyvinuta pomocí vzdálené komunikace rozhraní .NET. Skládá se ze serveru, který je cílen .NET Framework 4, který implementuje kontrakt s obecnými typy a dvěma různými klienty, jeden cílí .NET Framework 2,0 a jiný cílí .NET Framework 4.  
  
 Server připojí <xref:System.Runtime.Serialization.SerializationBinder> k binárnímu formátovacímu modulu, aby bylo možné změnit verzi typů odpovídající serializaci, aby oba klienti mohli tyto typy rekonstruovat správně.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Chcete-li spustit klienta, klikněte pravým tlačítkem myši na řešení, SBGenericsVTS (6 projektů) a pak vyberte **vlastnosti**.  
  
2. V možnosti **společné vlastnosti**vyberte možnost **projekt po spuštění**a pak vyberte **více projektů po spuštění**.  
  
3. Nejprve vyberte **Server** a pak **Client20** a pak **Client40**. Vyberte akci **Spustit** pro tyto tři projekty a nechejte nastavenou možnost **žádná**.  
  
4. Klikněte na **OK** a potom stisknutím klávesy F5 spusťte ukázku.
