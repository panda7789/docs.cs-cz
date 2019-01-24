---
title: Důležité informace o zabezpečení a vzdálené komunikaci
ms.date: 03/30/2017
helpviewer_keywords:
- code security, remoting
- remoting, security
- security [.NET Framework], remoting
- secure coding, remoting
ms.assetid: 125d2ab8-55a4-4e5f-af36-a7d401a37ab0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 39b7bcec1196a59c47717ec2b5622ca8e0d3cdfc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54591974"
---
# <a name="security-and-remoting-considerations"></a>Důležité informace o zabezpečení a vzdálené komunikaci
Vzdálená komunikace umožňuje nastavit transparentní volání mezi doménami aplikace, procesy nebo počítače. Procházení zásobníku zabezpečení přístupu kódu, ale nemůže překročit hranice procesu nebo počítače (platí mezi doménami aplikace stejného procesu).  
  
 Všechny třídy, která se dá použít vzdáleně (odvozený od <xref:System.MarshalByRefObject> třídy) musí nést odpovědnost za zabezpečení. Buď kód byste měli použít pouze ve uzavřené prostředí, kde volající kód může být implicitně důvěryhodné, nebo Vzdálená volání by se měly navrhovat tak, aby se nevztahují chráněného kódem mimo položku, která se dá použít speciálně.  
  
 Obecně platí, které byste nikdy neměli zveřejňovat metody, vlastnosti nebo události, které jsou chráněné službou deklarativní [LinkDemand](../../../docs/framework/misc/link-demands.md) a <xref:System.Security.Permissions.SecurityAction.InheritanceDemand> kontroly zabezpečení. U vzdálené komunikace nejsou vynucená těmito kontrolami. Další kontroly zabezpečení, jako například <xref:System.Security.Permissions.SecurityAction.Demand>, [Assert](../../../docs/framework/misc/using-the-assert-method.md), a tak dále fungovat mezi doménami aplikace v rámci procesu, ale nebudou fungovat ve scénářích mezi procesy nebo mezi počítači.  
  
## <a name="protected-objects"></a>Chráněné objekty  
 Některé objekty uložení stavu zabezpečení sama o sobě. Tyto objekty by neměl být předán nedůvěryhodný kód, který by pak získat autorizační zabezpečení nad rámec své vlastní oprávnění.  
  
 Jedním z příkladů je vytváření <xref:System.IO.FileStream> objektu. <xref:System.Security.Permissions.FileIOPermission> Je požadováno v okamžiku vytvoření a pokud se aktivace podaří, je vrácen objekt souboru. Ale pokud tento odkaz na objekt je předán do kódu bez oprávnění k souboru, objekt bude moct číst a zapisovat do tohoto konkrétního souboru.  
  
 Nejjednodušší defense pro takový objekt je stejný požadovat **FileIOPermission** jakéhokoli kódu, který se snaží získat odkaz na objekt prostřednictvím veřejného rozhraní API elementu.  
  
## <a name="application-domain-crossing-issues"></a>Problémy křížení domén aplikace  
 Izolace kódu ve spravovaném hostitelském prostředí, je běžné vytvořit více podřízených domén aplikace s explicitní zásady snížení úrovně oprávnění pro různá sestavení. Ale zásady pro tato sestavení zůstane beze změny ve výchozí doméně aplikace. Pokud jeden z podřízených domén aplikace lze vynutit výchozí domény aplikace se načíst sestavení, dojde ke ztrátě efekt izolace kódu a typy nuceně načtené sestavení budou moct spouštět kód na vyšší úrovni důvěryhodnosti.  
  
 Domény aplikace můžete vynutit jiné doméně aplikace k načtení sestavení a spuštění kódu obsažených voláním proxy objekt hostované v jiné doméně aplikace. Získat proxy aplikací. mezi doménami, musíte distribuovat doménu aplikace objektu hostování jedna prostřednictvím volání parametr nebo návratovou hodnotu metody. Nebo, pokud doména aplikace byla právě vytvořena, má autor proxy <xref:System.AppDomain> objektu ve výchozím nastavení. Pokud chcete vyhnout přerušení izolace kódu, proto by neměl domény aplikace s vyšší úroveň důvěryhodnosti distribuovat odkazy na objekty zařazen podle odkazu (instance tříd odvozených z <xref:System.MarshalByRefObject>) ve své doméně do domény aplikace s nižší úrovně důvěryhodnosti.  
  
 Výchozí domény aplikace obvykle vytvoří podřízené domény aplikace s objekt ovládacího prvku v každém z nich. Objekt ovládacího prvku spravuje nové aplikační doméně a někdy trvá objednávky z výchozí domény aplikace, ale nemůže kontaktovat doménu přímo. V některých případech výchozí domény aplikace volá jeho proxy objekt ovládacího prvku. Mohou však existovat případy, ve které je nezbytné pro objekt ovládacího prvku pro zpětné volání do výchozí domény aplikace. V těchto případech výchozí domény aplikace předá objekt zpětného volání marshal-by-reference do konstruktoru objektu ovládacího prvku. Je odpovědností objekt ovládacího prvku k ochraně tohoto proxy serveru. Pokud objekt ovládacího prvku umístit proxy serveru na veřejné statické pole veřejné třídy nebo jinak veřejně zpřístupnit proxy server, to by otevřete nebezpečné mechanismus pro jiný kód zavolá zpět do výchozí domény aplikace. Z tohoto důvodu jsou vždy objekty ovládací prvek implicitně důvěryhodná udržovat privátní proxy serveru.  
  
## <a name="see-also"></a>Viz také:
- [Pokyny pro zabezpečené kódování](../../../docs/standard/security/secure-coding-guidelines.md)
