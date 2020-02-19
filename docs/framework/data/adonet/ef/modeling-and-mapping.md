---
title: Modelování a mapování
ms.date: 03/30/2017
ms.assetid: ec8a9515-3708-4cde-a688-4d8e6975f150
ms.openlocfilehash: e70411bb9c9797ee348aeef055c9af20ea092ae3
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77450593"
---
# <a name="modeling-and-mapping"></a>Modelování a mapování
V Entity Framework můžete definovat koncepční model, model úložiště a mapování mezi nimi způsobem, který nejlépe vyhovuje vaší aplikaci. Nástroje model EDM (Entity Data Model) v aplikaci Visual Studio umožňují vytvořit. [soubor EDMX](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100)) z databáze nebo grafického modelu a poté tento soubor aktualizovat, když se změní databáze nebo model.  
  
 Počínaje Entity Framework 4,1 můžete také vytvořit model programově pomocí Code Firstho vývoje. Existují dva různé scénáře vývoje Code First. V obou případech vývojář definuje model pomocí kódování .NET Framework definice tříd a pak volitelně určuje dodatečné mapování nebo konfiguraci pomocí datových poznámek nebo rozhraní Fluent API.  
  
 Další informace najdete v tématu [Vytvoření modelu](/ef/ef6/modeling/).  
  
 Můžete také použít generátor EDM, který je součástí .NET Framework. EdmGen. exe generuje soubory. csdl,. ssdl a. MSL z existujícího zdroje dat. Můžete také ručně vytvořit model a mapování obsahu. Další informace najdete v tématu [generátor EDM (EdmGen. exe)](edm-generator-edmgen-exe.md).
