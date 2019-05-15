---
title: Nasazení projektu knihovny WCF
ms.date: 03/30/2017
ms.assetid: 9f9222fe-d358-443c-9a49-12c5498e35e7
ms.openlocfilehash: 0400fc9ec5a5629139348709bbd3a5554ce251c7
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65593353"
---
# <a name="deploying-a-wcf-library-project"></a>Nasazení projektu knihovny WCF
Toto téma popisuje, jak nasadit projekt knihovny služby Windows Communication Foundation (WCF).  
  
## <a name="deploying-a-wcf-service-library"></a>Nasazení knihovny služby WCF  
 Knihovna služby WCF je dynamická knihovna (DLL). V důsledku toho nelze jej provést sama o sobě. Musí být nasazené do hostitelského prostředí. Další informace o tomto procesu najdete v tématu [hostování a využívání služby WCF](https://go.microsoft.com/fwlink/?LinkId=99932).  
  
 Knihovna služby WCF je možné nasadit stejně jako jakoukoli jinou službu WCF. Nezapomínejte, že rozhraní .NET Framework nepodporuje konfiguraci pro knihovny DLL. <xref:System.Configuration> podporuje jeden soubor konfigurace domény aplikace. Projekt knihovny služby WCF není toto omezení přepínat tím, že poskytuje soubor App.config pro knihovnu během vývoje. Soubor App.config však nebyl rozpoznán po nasazení.  
  
 Budete muset přesunout konfigurace kódu do konfiguračního souboru rozpoznávaných hostitelského prostředí. Hostování na vlastním byste zkopírovat obsah konfiguračního souboru aplikace do souboru App.config hostující spustitelný soubor. Pokud použijete k hostování vaší služby IIS, měli byste zkopírovat obsah souboru App.config do souboru Web.config virtuálního adresáře.
