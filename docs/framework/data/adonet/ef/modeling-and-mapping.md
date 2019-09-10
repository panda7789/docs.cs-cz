---
title: Modelování a mapování
ms.date: 03/30/2017
ms.assetid: ec8a9515-3708-4cde-a688-4d8e6975f150
ms.openlocfilehash: 133539ab1b6d6f2f0ab3f8deed5b22240c2bb07e
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854402"
---
# <a name="modeling-and-mapping"></a>Modelování a mapování
V Entity Framework můžete definovat koncepční model, model úložiště a mapování mezi nimi způsobem, který nejlépe vyhovuje vaší aplikaci. Nástroje model EDM (Entity Data Model) v aplikaci Visual Studio umožňují vytvořit. [soubor EDMX](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100)) z databáze nebo grafického modelu a poté tento soubor aktualizovat, když se změní databáze nebo model.  
  
 Počínaje Entity Framework 4,1 můžete také vytvořit model programově pomocí Code Firstho vývoje. Existují dva různé scénáře vývoje Code First. V obou případech vývojář definuje model pomocí kódování .NET Framework definice tříd a pak volitelně určuje dodatečné mapování nebo konfiguraci pomocí datových poznámek nebo rozhraní Fluent API.  
  
 Další informace najdete v tématu [Vytvoření a mapování koncepčního modelu](https://go.microsoft.com/fwlink/?LinkId=235016).  
  
 Můžete také použít generátor EDM, který je součástí .NET Framework. EdmGen. exe generuje soubory. csdl,. ssdl a. MSL z existujícího zdroje dat. Můžete také ručně vytvořit model a mapování obsahu. Další informace najdete v tématu [generátor EDM (EdmGen. exe)](edm-generator-edmgen-exe.md).
