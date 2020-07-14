---
title: Důležité informace o zabezpečení a vzdálené komunikaci
description: Přečtěte si o otázkách zabezpečení v souvislosti se vzdálenou komunikací, která umožňuje nastavit transparentní volání mezi doménami aplikace, procesy nebo počítači.
ms.date: 03/30/2017
helpviewer_keywords:
- code security, remoting
- remoting, security
- security [.NET Framework], remoting
- secure coding, remoting
ms.assetid: 125d2ab8-55a4-4e5f-af36-a7d401a37ab0
ms.openlocfilehash: 029f9863ebed94805675b629be7eb10963a7b689
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281391"
---
# <a name="security-and-remoting-considerations"></a>Důležité informace o zabezpečení a vzdálené komunikaci
Vzdálená komunikace umožňuje nastavit transparentní volání mezi doménami aplikace, procesy nebo počítači. Procházení zásobníku zabezpečení přístupu kódu ale nemůže mezi procesy nebo počítači překročit hranice (používá se mezi aplikačními doménami stejného procesu).  
  
 Jakákoliv třída, která je vzdáleně (odvozená od <xref:System.MarshalByRefObject> třídy), musí převzít zodpovědnost za zabezpečení. Kód by měl být použit pouze v uzavřených prostředích, kde může být volající kód implicitně důvěryhodný, nebo by volání vzdálené komunikace měla být navržena tak, aby nepředmětoval chráněný kód na vnější položku, která by mohla být použita škodlivě.  
  
 Obecně by nikdy neměly vystavovat metody, vlastnosti nebo události, které jsou chráněny pomocí deklarativního [LinkDemand](link-demands.md) a <xref:System.Security.Permissions.SecurityAction.InheritanceDemand> kontroly zabezpečení. U vzdálené komunikace nejsou tyto kontroly vynutily. Další kontroly zabezpečení, například <xref:System.Security.Permissions.SecurityAction.Demand> , [Assert](using-the-assert-method.md)a tak dále, pracují mezi doménami aplikace v rámci procesu, ale nefungují ve scénářích mezi procesy a mezi počítači.  
  
## <a name="protected-objects"></a>Chráněné objekty  
 Některé objekty samy uchovávají stav zabezpečení. Tyto objekty by neměly být předány nedůvěryhodnému kódu, což by pak získalo autorizaci zabezpečení nad rámec svých vlastních oprávnění.  
  
 Jedním z příkladů je vytvoření <xref:System.IO.FileStream> objektu. <xref:System.Security.Permissions.FileIOPermission>Je vyžádané v době vytvoření a v případě úspěchu je vrácen objekt File. Pokud je však tento odkaz na objekt předán do kódu bez oprávnění k souboru, bude objekt moci číst a zapisovat do tohoto konkrétního souboru.  
  
 Nejjednodušší obrana takového objektu je požadovat stejné **FileIOPermission** jakéhokoli kódu, který se snaží získat odkaz na objekt prostřednictvím veřejného prvku rozhraní API.  
  
## <a name="application-domain-crossing-issues"></a>Problémy při křížení domény aplikace  
 Chcete-li izolovat kód ve spravovaných hostujících prostředích, je běžné generovat více domén podřízené aplikace s explicitními zásadami, které snižují úrovně oprávnění pro různá sestavení. Nicméně zásady pro tato sestavení zůstávají beze změny ve výchozí aplikační doméně. Pokud jedna z podřízených domén aplikace může vynutit, aby výchozí doména aplikace načetla sestavení, účinek izolace kódu je ztracen a typy v nuceně načteném sestavení budou moci spustit kód na vyšší úrovni důvěryhodnosti.  
  
 Doména aplikace může vynutit jinou aplikační doménu, aby načetla sestavení a kód, který je v něm obsažený, voláním proxy na objekt hostovaný v jiné doméně aplikace. Aby bylo možné získat proxy server mezi aplikačními aplikacemi, musí doména aplikace, která je hostitelem objektu, distribuovat jednu prostřednictvím parametru volání metody nebo návratové hodnoty. Nebo, pokud byla doména aplikace právě vytvořena, tvůrce má <xref:System.AppDomain> ve výchozím nastavení proxy objekt k objektu. Proto k tomu, aby nedošlo k narušení izolace kódu, by doména aplikace s vyšší úrovní důvěryhodnosti neměla distribuovat odkazy na objekty zařazování podle referencí (instance tříd odvozené z <xref:System.MarshalByRefObject> ) ve své doméně do domén aplikace s nižšími úrovněmi důvěryhodnosti.  
  
 Výchozí aplikační doména obvykle vytváří podřízené domény aplikace s objektem ovládacího prvku v každém z nich. Řídicí objekt spravuje novou doménu aplikace a občas bere objednávky z výchozí domény aplikace, ale nemůže ve skutečnosti kontaktovat doménu přímo. V některých případech výchozí doména aplikace volá svůj proxy do objektu Control. Nicméně mohou nastat případy, kdy je nutné, aby objekt ovládacího prvku volal zpět do výchozí domény aplikace. V těchto případech výchozí doména aplikace předá objekt zpětného volání zařazovacího odkazu do konstruktoru objektu ovládacího prvku. Je zodpovědností za objekt Control k ochraně tohoto proxy serveru. Pokud měl řídicí objekt umístit proxy na veřejné statické pole veřejné třídy nebo jinak veřejně vystavení proxy serveru, tím by se otevřel nebezpečný mechanismus pro jiný kód pro volání zpět do výchozí domény aplikace. Z tohoto důvodu jsou objekty ovládacího prvku vždy implicitně důvěryhodné, aby zůstaly proxy privátní.  
  
## <a name="see-also"></a>Viz také

- [Pokyny pro zabezpečené kódování](../../standard/security/secure-coding-guidelines.md)
