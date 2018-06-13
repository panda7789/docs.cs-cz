---
title: Nasazení projektu knihovny WCF
ms.date: 03/30/2017
ms.assetid: 9f9222fe-d358-443c-9a49-12c5498e35e7
ms.openlocfilehash: fb400a4d1ebba691222ad7fc9d2c09f1051591da
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33803020"
---
# <a name="deploying-a-wcf-library-project"></a>Nasazení projektu knihovny WCF
Toto téma popisuje, jak můžete nasazení projektu knihovny služby Windows Communication Foundation (WCF).  
  
## <a name="deploying-a-wcf-service-library"></a>Nasazení knihovny služby WCF  
 Knihovna služby WCF je dynamická knihovna (DLL). Jako takový ho nelze provést na svou vlastní. Musí být nasazeny do hostitelského prostředí. Další informace o tomto procesu najdete v tématu [hostitelský a využívání služby WCF](http://go.microsoft.com/fwlink/?LinkId=99932).  
  
 Knihovny služby WCF můžete nasadit stejně jako ostatní služby WCF. Ale pozor který [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] nepodporuje konfiguraci pro knihovny DLL. <xref:System.Configuration> podporuje jeden soubor konfigurace pro doménu AppDomain. Projektu knihovny WCF služby nebude toto omezení tím, že poskytuje soubor App.config pro knihovnu během vývoje. Soubor App.config se však nerozpoznal po nasazení.  
  
 Je nutné přesunout konfigurace kódu do konfiguračního souboru rozpoznáno hostitelského prostředí. Pro vlastní hostování, měli byste zkopírovat obsah souboru App.config do souboru App.config hostování spustitelného souboru. Pokud použijete k hostování služby IIS, měli byste zkopírovat obsah souboru App.config v souboru Web.config virtuálního adresáře.
