---
title: Modelování a mapování
ms.date: 03/30/2017
ms.assetid: ec8a9515-3708-4cde-a688-4d8e6975f150
ms.openlocfilehash: 81080c416fd18c51be6626cb70a23073e049051d
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45593508"
---
# <a name="modeling-and-mapping"></a>Modelování a mapování
V [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], můžete definovat konceptuální model, úložiště modelu a mapování mezi těmito dvěma způsobem, která nejlépe vyhovuje vaší aplikace. Nástroje modelu dat Entity v sadě Visual Studio umožňují vytvářet. [souboru edmx](https://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4) z databáze nebo grafické modelu a aktualizujete soubor při změně databáze nebo model.  
  
 Od verze Entity Framework 4.1 můžete také vytvořit model programově pomocí vývoje Code First. Existují dva různé scénáře vývoje Code First. V obou případech se vývojář definuje model kódu pro definice tříd rozhraní .NET Framework a poté volitelně určuje dodatečné mapování nebo konfigurace s použitím datových poznámek nebo rozhraní fluent API.  
  
 Další informace najdete v tématu [vytváření a mapování koncepční Model](https://go.microsoft.com/fwlink/?LinkId=235016).  
  
 Můžete také použít Generátor EDM, který je součástí [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)]. EdmGen.exe generuje .csdl, .ssdl a .msl soubory z existujícího zdroje dat. Můžete také ručně vytvořit modelu a mapování obsahu. Další informace najdete v tématu [generátor EDM (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md).
