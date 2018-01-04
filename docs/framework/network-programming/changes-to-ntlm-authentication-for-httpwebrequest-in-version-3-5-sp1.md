---
title: "Změny v ověřování protokolem NTLM pro HttpWebRequest v verze 3.5 SP1."
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8bf0b428-5a21-4299-8d6e-bf8251fd978a
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 239834a732fe3bc1cb3e8e7f1d126d26c210d1f6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="changes-to-ntlm-authentication-for-httpwebrequest-in-version-35-sp1"></a>Změny v ověřování protokolem NTLM pro HttpWebRequest v verze 3.5 SP1.
Byly provedeny změny zabezpečení v rozhraní .NET Framework verze 3.5 SP1 a novější, vliv na způsob integrované ověřování systému Windows, které se provádí ověřování <xref:System.Net.HttpWebRequest>, <xref:System.Net.HttpListener>, <xref:System.Net.Security.NegotiateStream>, a související třídy v oboru názvů System.Net. Tyto změny mohou ovlivnit aplikace, které používají tyto třídy webové požadavky a odpovědi přijímat, kde se používá integrované ověřování systému Windows, které jsou založené na protokolu NTLM. Tato změna může ovlivnit webové servery a klientské aplikace, které jsou nakonfigurovány pro použití integrovaného ověřování systému Windows.  
  
## <a name="overview"></a>Přehled  
 Návrh integrované ověřování systému Windows umožňuje některé odpovědí přihlašovacích údajů se univerzální, znamená, může být znovu použít nebo předají. Pokud tato konkrétní funkce není nutné, ověřovací protokoly by měli postupovat konkrétní informace o cílové, jakož i kanál konkrétní informace. Služby jim pak můžou rozšířené ochrany a zajistit, že odpovědí přihlašovacích údajů obsahovat informace o konkrétní služby například hlavní název služby (SPN). Pomocí těchto informací v výměnu přihlašovacích údajů budou moci lepší ochranu proti zneužití přihlašovacích údajů odpovědi, které může být nesprávně získáno služby.  
  
 Několik součástí v <xref:System.Net> a <xref:System.Net.Security> obory názvů provést integrované ověřování systému Windows jménem volající aplikace. Tato část popisuje změny součástí System.NET – přidání rozšířené ochrany v jejich používání integrovaného ověřování systému Windows.  
  
## <a name="changes"></a>Změny  
 Proces ověřování NTLM používá s integrované ověřování systému Windows obsahuje výzvy od cílového počítače a odeslat zpátky do klientského počítače. Když počítač obdrží výzvu, že samotný vygeneroval, ověřování selže, pokud připojení je připojení zpětné smyčky (adresu IPv4 127.0.0.1, např.).  
  
 Při přístupu k služby spuštěné na webovém serveru interní, je běžné pro přístup ke službě pomocí podobné http://contoso/service nebo https://contoso/service adresy URL. Název "contoso" není často název počítače, na kterém je nasazený službu. <xref:System.Net> a související obory názvů podporovat použití služby Active Directory, DNS, pro rozhraní NetBIOS, místní počítač hostuje souboru (obvykle WINDOWS\system32\drivers\etc\hosts, např.) nebo soubor lmhosts v místním počítači (obvykle WINDOWS\system32\ drivers\etc\lmhosts, např.) k překladu názvů na adresy. Název "contoso" je vyřešit tak, aby požadavky odeslané na "contoso" se odesílají do počítače příslušného serveru.  
  
 Když nakonfigurovaný pro velká nasazení, je také běžné název jednoho virtuálního serveru, který má být poskytnut do nasazení s základní názvy počítačů nikdy používané klientské aplikace a koncoví uživatelé. Může například volání www.contoso.com serveru, ale v interní síti jednoduše použijte "contoso". Tento název se nazývá hlavičku hostitele v žádosti webového klienta. Podle specifikace protokolu HTTP určuje pole hlavičky požadavku hostitel Internetu hostitele a port číslo požadovaný prostředek. Tyto informace se získávají z původní URI zadané uživatelem nebo odkazující prostředků (obvykle adresu URL protokolu HTTP). V rozhraní .NET Framework verze 4, tyto informace můžete nastavit také klienta pomocí nové <xref:System.Net.HttpWebRequest.Host%2A> vlastnost.  
  
 <xref:System.Net.AuthenticationManager> Třídy řídí součásti spravované ověřování ("moduly"), které jsou používány <xref:System.Net.WebRequest> odvozené třídy a <xref:System.Net.WebClient> třídy. <xref:System.Net.AuthenticationManager> Třída poskytuje vlastnosti, která zveřejňuje <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A?displayProperty=nameWithType> objekt, indexovat pomocí řetězce URI, pro aplikace pro zadat vlastní řetězec názvu SPN pro použití při ověřování.  
  
 Verze 3.5 SP1 teď použity výchozí hodnoty pro zadání názvu hostitele v adrese URL žádosti v hlavní název služby v ověřování protokolem NTLM (NT LAN Manager) systému exchange, kdy <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A> není nastavena vlastnost. Název hostitele použít v adrese URL žádosti může lišit od Zadaná hlavička hostitele v <xref:System.Net.HttpRequestHeader?displayProperty=nameWithType> v požadavku klienta. Název hostitele použít v adrese URL požadavku se může lišit od skutečným názvem hostitele serveru, název počítače serveru, jeho IP adresu nebo adresu zpětné smyčky. V těchto případech se nezdaří Windows žádosti o ověření. Chcete-li tento problém vyřešit, je třeba upozornit Windows, který používá název hostitele v adrese URL žádosti v klientovi požadavku ("contoso", například) je ve skutečnosti alternativní název pro místní počítač.  
  
 Existuje několik možných metod pro serverové aplikace, chcete-li vyřešit tuto změnu. Doporučený přístup je pro mapování názvu hostitele v adrese URL požadavku na použité `BackConnectionHostNames` klíče v registru na serveru. `BackConnectionHostNames` Klíč registru se obvykle používají pro mapování názvu hostitele na adresu zpětné smyčky. Kroky jsou uvedeny níže.  
  
 Pokud chcete zadat názvy hostitelů, které jsou mapované na adresu zpětné smyčky a může připojit k webům na místním počítači, postupujte takto:  
  
 1. Klikněte na tlačítko Start, klikněte na tlačítko spustit, zadejte příkaz regedit a klikněte na tlačítko OK.  
  
 2. V editoru registru vyhledejte a pak klikněte na následující klíč registru:  
  
 `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa\MSV1_0`  
  
 3. Klikněte pravým tlačítkem na MSV1_0, přejeďte na volbu Nový a klikněte na položku víceřetězcovou hodnotu.  
  
 4. Typ `BackConnectionHostNames`, a stiskněte klávesu ENTER.  
  
 5. Klikněte pravým tlačítkem na `BackConnectionHostNames`a poté klikněte na Upravit.  
  
 6. V poli Údaj hodnoty zadejte název hostitele nebo názvy hostitelů pro weby (název hostitele použít v adrese URL požadavku), které jsou v místním počítači a pak klikněte na tlačítko OK.  
  
 7. Ukončete program Editor registru a potom restartujte službu spustit a spusťte příkaz IISReset.  
  
 Méně bezpečné pracovní přibližně je zakázat kontrolu zpětné smyčky, jak je popsáno v [http://support.microsoft.com/kb/896861](http://go.microsoft.com/fwlink/?LinkID=179657). Zakáže ochranu proti útokům na reflexi. Proto je lepší omezit sadu alternativní názvy pouze ty, které očekáváte, že má počítač ve skutečnosti použít.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A?displayProperty=nameWithType>  
 <xref:System.Net.HttpRequestHeader?displayProperty=nameWithType>  
 <xref:System.Net.HttpWebRequest.Host%2A?displayProperty=nameWithType>
