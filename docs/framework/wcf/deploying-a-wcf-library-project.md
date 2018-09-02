---
title: Nasazení projektu knihovny WCF
ms.date: 03/30/2017
ms.assetid: 9f9222fe-d358-443c-9a49-12c5498e35e7
ms.openlocfilehash: 1ba26a7e68fe262dc5f4f569647af1ebb94e03a8
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43387223"
---
# <a name="deploying-a-wcf-library-project"></a>Nasazení projektu knihovny WCF
Toto téma popisuje, jak nasadit projekt knihovny služby Windows Communication Foundation (WCF).  
  
## <a name="deploying-a-wcf-service-library"></a>Nasazení knihovny služby WCF  
 Knihovna služby WCF je dynamická knihovna (DLL). V důsledku toho nelze jej provést sama o sobě. Musí být nasazené do hostitelského prostředí. Další informace o tomto procesu najdete v tématu [hostování a využívání služby WCF](https://go.microsoft.com/fwlink/?LinkId=99932).  
  
 Knihovna služby WCF je možné nasadit stejně jako jakoukoli jinou službu WCF. Nezapomínejte, že [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] nepodporuje konfiguraci pro knihovny DLL. <xref:System.Configuration> podporuje jeden soubor konfigurace domény aplikace. Projekt knihovny služby WCF není toto omezení přepínat tím, že poskytuje soubor App.config pro knihovnu během vývoje. Soubor App.config však nebyl rozpoznán po nasazení.  
  
 Budete muset přesunout konfigurace kódu do konfiguračního souboru rozpoznávaných hostitelského prostředí. Hostování na vlastním byste zkopírovat obsah konfiguračního souboru aplikace do souboru App.config hostující spustitelný soubor. Pokud použijete k hostování vaší služby IIS, měli byste zkopírovat obsah souboru App.config do souboru Web.config virtuálního adresáře.
