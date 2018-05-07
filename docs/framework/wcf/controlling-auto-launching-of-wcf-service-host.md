---
title: Ovládání automatického spouštění hostitele služeb WCF
ms.date: 03/30/2017
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
ms.openlocfilehash: fe936ee3ff42b586c733de597de808b86f3e2575
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a>Ovládání automatického spouštění hostitele služeb WCF
Můžete ovládat funkce automatického spouštění hostitele služeb Windows Communication Foundation (WCF) (WcfSvcHost.exe) pro [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] projektu knihovny služby, při ladění projektu pro jiné ve stejném řešení sady Visual Studio obsahující více projektů .  
  
 To pokud chcete udělat, klikněte pravým tlačítkem myši [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] projektu služby v **Průzkumníku řešení**, zvolte **vlastnosti**a klikněte na tlačítko **WCF možnosti** kartě. **Spustit hostitel služby WCF při ladění jiného projektu ve stejném řešení** zaškrtávací políčko je dostupné ve výchozím nastavení. Můžete vymazat pole tak, aby [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hostitele služby pro tento konkrétní projekt není spustí, když je ve stejném řešení ladit jiného projektu.  
  
 Toto chování neovlivňuje ladění F5 nebo funkce Přidat odkaz na službu pro tento projekt.  
  
 Tato možnost je dostupná na následujících projektech:  
  
-   [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Projekt knihovny služby.  
  
-   Projekt knihovny služby sekvenční pracovní postup.  
  
-   Projekt knihovny služby stavu počítače pracovního postupu.  
  
-   Syndikace projektu knihovny služby.  
  
## <a name="see-also"></a>Viz také  
 [Hostitel služby WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
