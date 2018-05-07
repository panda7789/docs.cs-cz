---
title: Nasazení projektu knihovny WCF
ms.date: 03/30/2017
ms.assetid: 9f9222fe-d358-443c-9a49-12c5498e35e7
ms.openlocfilehash: 08a1d794aeeea1a41cd1eb3abf298f3f4a0f6d15
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="deploying-a-wcf-library-project"></a>Nasazení projektu knihovny WCF
Toto téma popisuje, jak můžete nasazení projektu knihovny služby Windows Communication Foundation (WCF).  
  
## <a name="deploying-a-wcf-service-library"></a>Nasazení knihovny služby WCF  
 A [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] knihovny služby je dynamická knihovna (DLL). Jako takový ho nelze provést na svou vlastní. Musí být nasazeny do hostitelského prostředí. Další informace o tomto procesu najdete v tématu [hostitelský a využívání služby WCF](http://go.microsoft.com/fwlink/?LinkId=99932).  
  
 A [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] knihovny služby se dá nasadit jako libovolný jiný [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby. Ale pozor který [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] nepodporuje konfiguraci pro knihovny DLL. <xref:System.Configuration> podporuje jeden soubor konfigurace pro doménu AppDomain. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Projektu knihovny služby nebude toto omezení tím, že poskytuje soubor App.config pro knihovnu během vývoje. Soubor App.config se však nerozpoznal po nasazení.  
  
 Je nutné přesunout konfigurace kódu do konfiguračního souboru rozpoznáno hostitelského prostředí. Pro vlastní hostování, měli byste zkopírovat obsah souboru App.config do souboru App.config hostování spustitelného souboru. Pokud použijete k hostování služby IIS, měli byste zkopírovat obsah souboru App.config v souboru Web.config virtuálního adresáře.
