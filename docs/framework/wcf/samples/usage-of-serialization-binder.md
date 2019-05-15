---
title: Použití vazače serializace
ms.date: 03/30/2017
ms.assetid: ab46c087-200c-45bf-9c95-5a6cda6e8b98
ms.openlocfilehash: 677decebcf444fed95311bd02acf8a96e0a4eca9
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591776"
---
# <a name="usage-of-serialization-binder"></a>Použití vazače serializace
Tento příklad ukazuje způsob použití <xref:System.Runtime.Serialization.SerializationBinder> chcete změnit verzi obecného typu, pokud je serializována.  
  
## <a name="demonstrates"></a>Demonstruje  
 <xref:System.Runtime.Serialization.SerializationBinder>, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>  
  
## <a name="discussion"></a>Diskuse  
 Tento příklad ukazuje, jak dvě entity, jsou cílení na různé verze rozhraní .NET Framework mohou komunikovat pomocí binární formátovací modul a vazače serializace.  
  
 Vývoj této ukázce proběhl pomocí vzdálené komunikace .NET. Ukázka se skládá ze serveru cílení [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)], který implementuje kontrakt s obecné typy a dvou různých klientů, jedna cílení [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)] a cílí na jinou [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)].  
  
 Server připojí <xref:System.Runtime.Serialization.SerializationBinder> na binární formátovací modul, abyste mohli změnit verzi typy odpovídajícím způsobem na serializace, takže oba klienti může deserializovat tyto typy správně.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1. Ke spuštění klienta, klikněte pravým tlačítkem na řešení, SBGenericsVTS (6 projektů) a pak vyberte **vlastnosti**.  
  
2. V **společné vlastnosti**vyberte **spouštěný projekt**a pak vyberte **více projektů po spuštění**.  
  
3. Vyberte **Server** první, potom **Client20** a potom **Client40**. Vyberte **Start** akce do těchto tří projektů a ponechte zbývající nastavení **žádný**.  
  
4. Klikněte na tlačítko **OK** a potom stiskněte klávesu F5 ke spuštění ukázky.
