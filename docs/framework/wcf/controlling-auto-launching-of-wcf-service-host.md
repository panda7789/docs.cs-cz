---
title: Ovládání automatického spouštění hostitele služeb WCF
ms.date: 03/30/2017
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
ms.openlocfilehash: 63c3ca00c0cdc0b28de0fe245b616acd04ca50fe
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a>Ovládání automatického spouštění hostitele služeb WCF
Můžete ovládat funkce automatického spouštění hostitele služeb Windows Communication Foundation (WCF) (WcfSvcHost.exe) pro projekt knihovny služby WCF, při ladění projektu pro jiné ve stejném řešení sady Visual Studio obsahující více projektů.  
  
 Uděláte to tak, klikněte pravým tlačítkem na projekt služby WCF v **Průzkumníku řešení**, zvolte **vlastnosti**a klikněte na tlačítko **WCF možnosti** kartě. **Spustit hostitel služby WCF při ladění jiného projektu ve stejném řešení** zaškrtávací políčko je dostupné ve výchozím nastavení. Pole můžete vymazat tak, aby hostitel služby WCF pro tento konkrétní projekt není spustí, když je ve stejném řešení ladit jiného projektu.  
  
 Toto chování neovlivňuje ladění F5 nebo funkce Přidat odkaz na službu pro tento projekt.  
  
 Tato možnost je dostupná na následujících projektech:  
  
-   Projekt knihovny služby WCF.  
  
-   Projekt knihovny služby sekvenční pracovní postup.  
  
-   Projekt knihovny služby stavu počítače pracovního postupu.  
  
-   Syndikace projektu knihovny služby.  
  
## <a name="see-also"></a>Viz také  
 [Hostitel služby WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
