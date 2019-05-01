---
title: Modelování a mapování
ms.date: 03/30/2017
ms.assetid: ec8a9515-3708-4cde-a688-4d8e6975f150
ms.openlocfilehash: 847d518710b21df714343b541401ff7fc8443fb3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62034018"
---
# <a name="modeling-and-mapping"></a>Modelování a mapování
V [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], můžete definovat konceptuální model, úložiště modelu a mapování mezi těmito dvěma způsobem, která nejlépe vyhovuje vaší aplikace. Nástroje modelu dat Entity v sadě Visual Studio umožňují vytvářet. [souboru edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100)) z databáze nebo grafické modelu a aktualizujete soubor při změně databáze nebo model.  
  
 Od verze Entity Framework 4.1 můžete také vytvořit model programově pomocí vývoje Code First. Existují dva různé scénáře vývoje Code First. V obou případech se vývojář definuje model kódu pro definice tříd rozhraní .NET Framework a poté volitelně určuje dodatečné mapování nebo konfigurace s použitím datových poznámek nebo rozhraní fluent API.  
  
 Další informace najdete v tématu [vytváření a mapování koncepční Model](https://go.microsoft.com/fwlink/?LinkId=235016).  
  
 Můžete také použít Generátor EDM, který je součástí [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)]. EdmGen.exe generuje .csdl, .ssdl a .msl soubory z existujícího zdroje dat. Můžete také ručně vytvořit modelu a mapování obsahu. Další informace najdete v tématu [generátor EDM (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md).
