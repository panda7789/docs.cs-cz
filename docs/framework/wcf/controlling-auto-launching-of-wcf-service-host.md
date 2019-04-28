---
title: Ovládání automatického spouštění hostitele služeb WCF
ms.date: 03/30/2017
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
ms.openlocfilehash: 2fa060e567fba9bb5e6344b2c8fc67fb639ad0f7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61608447"
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a>Ovládání automatického spouštění hostitele služeb WCF
Můžete řídit funkce automatického spouštění hostitele služeb Windows Communication Foundation (WCF) (WcfSvcHost.exe) pro projekt knihovny služby WCF při ladění jiného projektu ve stejném řešení sady Visual Studio obsahuje více projektů.  
  
 Uděláte to tak, klikněte pravým tlačítkem na projekt služby WCF v **Průzkumníka řešení**, zvolte **vlastnosti**a klikněte na tlačítko **možnosti WCF** kartu. **Spuštění hostitele služby WCF při ladění jiného projektu ve stejném řešení** zaškrtávací políčko je dostupné ve výchozím nastavení. Do pole můžete vymazat tak, aby hostitel služby WCF pro tento konkrétní projekt není spuštěn při ladění jiného projektu ve stejném řešení.  
  
 Toto chování neovlivňuje ladění F5 nebo přidat odkaz na službu funkcích pro tento projekt.  
  
 Tato možnost je k dispozici pro následující projekty:  
  
- Projekt knihovny služby WCF.  
  
- Projekt knihovna služby sekvenčního pracovního postupu.  
  
- Projekt knihovny služby pracovního postupu stavového stroje.  
  
- Projekt knihovna služby syndikace.  
  
## <a name="see-also"></a>Viz také:

- [Hostitel služby WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
