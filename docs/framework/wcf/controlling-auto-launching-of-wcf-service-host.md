---
title: Ovládání automatického spouštění hostitele služeb WCF
ms.date: 03/30/2017
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
ms.openlocfilehash: 7f21cd7ea600277461146387b962a89ea0a8472b
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320630"
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a>Ovládání automatického spouštění hostitele služeb WCF
Můžete řídit schopnost automatického spouštění hostitele služby Windows Communication Foundation (WCF) pro projekt knihovny služby WCF (WcfSvcHost. exe), při ladění jiného projektu ve stejném řešení sady Visual Studio, které obsahuje více projektů.  
  
 Provedete to tak, že kliknete pravým tlačítkem na projekt služby WCF v **Průzkumník řešení**, zvolíte **vlastnosti**a kliknete na kartu **Možnosti WCF** . V případě, že je ve výchozím nastavení zaškrtnuté políčko **spustit hostitele služby WCF při ladění jiného projektu ve stejném řešení** , je povolené. Toto políčko můžete zrušit, aby se hostitel služby WCF pro tento konkrétní projekt nespustil při ladění jiného projektu ve stejném řešení.  
  
 Toto chování nemá vliv na ladění F5 ani Přidat odkaz na službu funkce pro tento projekt.  
  
 Tato možnost je k dispozici pro následující projekty:  
  
- Projekt knihovny služby WCF.  
  
- Projekt knihovny služby sekvenčního pracovního postupu  
  
- Projekt knihovny služby pracovního postupu stavového stroje  
  
- Projekt s knihovnou služby syndikace.  
  
## <a name="see-also"></a>Viz také:

- [Hostitel služby WCF (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md)
