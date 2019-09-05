---
title: Modelování a mapování
ms.date: 03/30/2017
ms.assetid: ec8a9515-3708-4cde-a688-4d8e6975f150
ms.openlocfilehash: 33064d35b7ac4c469df3ca6f0111cc84ef10eb08
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248489"
---
# <a name="modeling-and-mapping"></a>Modelování a mapování
[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]V nástroji můžete definovat koncepční model, model úložiště a mapování mezi dvěma způsoby, které nejlépe vyhovují vaší aplikaci. Nástroje model EDM (Entity Data Model) v aplikaci Visual Studio umožňují vytvořit. [soubor EDMX](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100)) z databáze nebo grafického modelu a poté tento soubor aktualizovat, když se změní databáze nebo model.  
  
 Počínaje Entity Framework 4,1 můžete také vytvořit model programově pomocí Code Firstho vývoje. Existují dva různé scénáře vývoje Code First. V obou případech vývojář definuje model pomocí kódování .NET Framework definice tříd a pak volitelně určuje dodatečné mapování nebo konfiguraci pomocí datových poznámek nebo rozhraní Fluent API.  
  
 Další informace najdete v tématu [Vytvoření a mapování koncepčního modelu](https://go.microsoft.com/fwlink/?LinkId=235016).  
  
 Můžete také použít generátor EDM, který je součástí .NET Framework. EdmGen. exe generuje soubory. csdl,. ssdl a. MSL z existujícího zdroje dat. Můžete také ručně vytvořit model a mapování obsahu. Další informace najdete v tématu [generátor EDM (EdmGen. exe)](edm-generator-edmgen-exe.md).
