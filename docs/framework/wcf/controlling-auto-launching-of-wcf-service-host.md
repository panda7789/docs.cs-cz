---
title: Ovládání automatického spouštění hostitele služeb WCF
ms.date: 03/30/2017
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
ms.openlocfilehash: f7f58a684449819fe945ad1ba5bff12f425c8294
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54712389"
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a>Ovládání automatického spouštění hostitele služeb WCF
Můžete řídit funkce automatického spouštění hostitele služeb Windows Communication Foundation (WCF) (WcfSvcHost.exe) pro projekt knihovny služby WCF při ladění jiného projektu ve stejném řešení sady Visual Studio obsahuje více projektů.  
  
 Uděláte to tak, klikněte pravým tlačítkem na projekt služby WCF v **Průzkumníka řešení**, zvolte **vlastnosti**a klikněte na tlačítko **možnosti WCF** kartu. **Spuštění hostitele služby WCF při ladění jiného projektu ve stejném řešení** zaškrtávací políčko je dostupné ve výchozím nastavení. Do pole můžete vymazat tak, aby hostitel služby WCF pro tento konkrétní projekt není spuštěn při ladění jiného projektu ve stejném řešení.  
  
 Toto chování neovlivňuje ladění F5 nebo přidat odkaz na službu funkcích pro tento projekt.  
  
 Tato možnost je k dispozici pro následující projekty:  
  
-   Projekt knihovny služby WCF.  
  
-   Projekt knihovna služby sekvenčního pracovního postupu.  
  
-   Projekt knihovny služby pracovního postupu stavového stroje.  
  
-   Projekt knihovna služby syndikace.  
  
## <a name="see-also"></a>Viz také:
- [Hostitel služby WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
