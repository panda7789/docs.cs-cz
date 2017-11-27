---
title: "Důležité informace o zabezpečení a vzdálené komunikaci"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code security, remoting
- remoting, security
- security [.NET Framework], remoting
- secure coding, remoting
ms.assetid: 125d2ab8-55a4-4e5f-af36-a7d401a37ab0
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 94942360aaa91a39c8f46414807490bcb6e0b093
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="security-and-remoting-considerations"></a>Důležité informace o zabezpečení a vzdálené komunikaci
Vzdálená komunikace umožňuje nastavit průhledné volání mezi doménami aplikace, procesy nebo počítače. Procházení zásobníku zabezpečení přístupu kódu však nemůže překročit hranice procesu nebo počítače (použít mezi doménami aplikací stejného procesu).  
  
 Všechny třídy, která je vzdáleně nastavitelné (odvozený od <xref:System.MarshalByRefObject> třída) musí převzít odpovědnost za účelem zabezpečení. Buď kód by měl použít pouze v uzavřené prostředích, kde může být implicitně důvěryhodné volající kód nebo Vzdálená volání by měly být navrženy tak, aby se není předmětem chráněný kód mimo položku, která lze zneužít.  
  
 Obecně platí, které byste nikdy neměli zveřejňovat metody, vlastnosti a události, které jsou chráněné pomocí deklarativní [LinkDemand](../../../docs/framework/misc/link-demands.md) a <xref:System.Security.Permissions.SecurityAction.InheritanceDemand> kontroly zabezpečení. S vzdálenou komunikaci nejsou tyto kontroly vynutí. Další kontroly zabezpečení, jako například <xref:System.Security.Permissions.SecurityAction.Demand>, [Assert](../../../docs/framework/misc/using-the-assert-method.md)a tak dále fungovat mezi doménami aplikací v rámci procesu, ale nefungují ve scénářích napříč procesem nebo počítači.  
  
## <a name="protected-objects"></a>Chráněných objektů  
 Některé objekty uložení stavu zabezpečení v sami. Tyto objekty by neměl být předána do nedůvěryhodné kód, který by pak získal autorizaci zabezpečení mimo vlastní oprávnění.  
  
 Příkladem je vytvoření <xref:System.IO.FileStream> objektu. <xref:System.Security.Permissions.FileIOPermission> Je požadováno v době vytvoření a pokud se aktivace podaří, je vrácen objekt souboru. Ale pokud odkaz na tento objekt je předán do kódu bez oprávnění k souboru, objekt bude moct číst a zapisovat do tohoto konkrétního souboru.  
  
 Nejjednodušší obrana pro takový objekt je požadovat stejný **FileIOPermission** jakéhokoli kódu, který se snaží získat odkaz na objekt prostřednictvím veřejného elementu rozhraní API.  
  
## <a name="application-domain-crossing-issues"></a>Překročení problémy v doméně aplikace  
 Když Pokud chcete izolovat kódu ve spravovaných prostředích hostingu, je běžné generovat více podřízených domén aplikace s explicitní zásad snížení úrovně oprávnění pro různé sestavení. Zásady pro tyto sestavení zůstává však beze změny ve výchozí doméně aplikace. Pokud jeden z podřízených domén aplikace může vynutit výchozí doménu aplikace pro načtení sestavení, dojde ke ztrátě účinku izolace kódu a typy vynucené načíst sestavení budou moci spustit kód na vyšší úrovni důvěryhodnosti.  
  
 Domény aplikace můžete vynutit jinou doménu aplikace pro načtení sestavení a spuštění kódu v něm obsažený voláním proxy server na objekt hostované v jiné doméně aplikace. Pokud chcete získat proxy aplikace. mezi doménami, musíte distribuovat hostování objektu domény aplikace jedna prostřednictvím volání metoda hodnotu parametru nebo return. Nebo, pokud doména aplikace byl právě vytvořen, Tvůrce má proxy server a <xref:System.AppDomain> objekt ve výchozím nastavení. Aby se zabránilo narušení izolace kódu, proto by nemělo domény aplikace s vyšší úrovní důvěryhodnosti distribuovat odkazy na objekty zařazené pomocí odkazu (instance třídy odvozené od <xref:System.MarshalByRefObject>) ve své doméně do domén aplikace s nižší úrovně důvěryhodnosti.  
  
 Výchozí doméně aplikace obvykle vytvoří podřízené domény aplikace s objekt ovládacího prvku v každé z nich. Objekt ovládacího prvku spravuje novou doménu aplikace a někdy trvá objednávky z výchozí doménu aplikace, ale nemůže kontaktovat domény přímo. V některých případech výchozí doméně aplikace volá jeho proxy objekt ovládacího prvku. Však může být případy, ve které je nezbytné pro objekt ovládacího prvku volat zpět na výchozí doméně aplikace. V těchto případech výchozí doméně aplikace předá objekt zpětného volání zařazování odkazem do konstruktoru objektu objekt ovládacího prvku. Je zodpovědností objekt ovládacího prvku, který chcete chránit tento proxy server. Pokud objekt ovládacího prvku umístit proxy server na veřejné statické pole veřejné třídy nebo jinak veřejně odhalí proxy server, to by otevře nebezpečná mechanismus pro jiný kód pro zpětné volání do výchozí doméně aplikace. Z tohoto důvodu jsou vždy objekty řízení implicitně důvěryhodné zachovat privátní proxy serveru.  
  
## <a name="see-also"></a>Viz také  
 [Pokyny pro zabezpečené kódování](../../../docs/standard/security/secure-coding-guidelines.md)
