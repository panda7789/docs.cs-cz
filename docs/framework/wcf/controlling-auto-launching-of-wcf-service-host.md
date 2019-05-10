---
title: Ovládání automatického spouštění hostitele služeb WCF
ms.date: 03/30/2017
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
ms.openlocfilehash: 806d85df2a7fff63704db755400b81cc2dc5c37b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64652079"
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
