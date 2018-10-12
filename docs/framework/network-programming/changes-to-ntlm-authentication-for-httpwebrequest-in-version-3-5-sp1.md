---
title: Změny v ověřování NTLM pro HttpWebRequest ve verzi 3.5 SP1
ms.date: 03/30/2017
ms.assetid: 8bf0b428-5a21-4299-8d6e-bf8251fd978a
author: mcleblanc
ms.author: markl
ms.openlocfilehash: d67dec8814dc659e012b55439c2c8debd21e03ed
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49122662"
---
# <a name="changes-to-ntlm-authentication-for-httpwebrequest-in-version-35-sp1"></a>Změny v ověřování NTLM pro HttpWebRequest ve verzi 3.5 SP1
Byly provedeny změny zabezpečení v rozhraní .NET Framework verze 3.5 SP1 a novější, které ovlivňují jak integrované ověřování zařizuje služba Windows <xref:System.Net.HttpWebRequest>, <xref:System.Net.HttpListener>, <xref:System.Net.Security.NegotiateStream>, a související třídy v oboru názvů System.Net. Tyto změny mohou ovlivnit aplikace, které používají tyto třídy pro vytvoření webových požadavků a přijímání odpovědí, kde se používá integrované ověřování Windows, které jsou založené na NTLM. Tato změna může ovlivnit, webové servery a klientské aplikace, které jsou nakonfigurovány pro použití integrovaného ověřování Windows.  
  
## <a name="overview"></a>Přehled  
 Návrh integrované ověřování Windows umožňuje některé přihlašovací údaje odpovědí univerzální, což znamená, můžete opakovaně používat nebo přeposílání. Pokud není nutné tuto funkci konkrétního návrhu, ověřovací protokoly by měli postupovat cíl konkrétní informace, jakož i konkrétní informace o kanálu. Služby potom můžete zadat Rozšířená ochrana k zajištění, že odpovědi přihlašovacích údajů obsahovat informace o konkrétní služby jako je například hlavní název služby (SPN). Pomocí těchto informací v výměnu přihlašovacích údajů služby budou moct lepší ochranu proti zneužití přihlašovacích údajů odpovědí, které může být nesprávně pocházet.  
  
 Více součástí <xref:System.Net> a <xref:System.Net.Security> obory názvů provést integrované ověřování Windows pro volající aplikaci. Tato část popisuje změny System.Net součástí, přidáte rozšířenou ochranu pomocí jejich používá integrované ověřování Windows.  
  
## <a name="changes"></a>Změny  
 Proces ověřování NTLM, použít pro integrované ověřování Windows zahrnuje challenge vydané do cílového počítače a odesílaných zpět do klientského počítače. Když počítač obdrží výzvu, že jej generovat samotný, ověřování se nezdaří, pokud propojení není back připojení smyčky (IPv4 adresu 127.0.0.1, příklad).  
  
 Při přístupu k služby spuštěné na interním webovém serveru, je společné pro přístup ke službě pomocí adresy URL podobná `http://contoso/service` nebo `https://contoso/service`. Název "contoso" není často název počítače, na kterém je nasazená služba. <xref:System.Net> a související obory názvů podporují pomocí služby Active Directory, DNS a NetBIOS, místní počítač hostuje soubor (obvykle WINDOWS\system32\drivers\etc\hosts, například) nebo soubor lmhosts místního počítače (obvykle WINDOWS\system32\ drivers\etc\lmhosts, například) k překladu názvů na adresy. Název "contoso" se vyřeší tak, aby požadavky odeslané na "contoso" se odesílají do počítače příslušný server.  
  
 Při konfiguraci pro velká nasazení, je také běžné, že název jednoho virtuálního serveru má být poskytnut do nasazení s základní názvy počítačů použita nikdy klientské aplikace i koncové uživatele. Například může volat www.contoso.com serveru, ale v interní síti jednoduše použít "contoso". Tento název se nazývá hlavičku hostitele v žádosti webového klienta. Podle specifikace protokolu HTTP určuje pole hlavičky požadavku hostitele Internet hostitele a port číslo požadovaný prostředek. Tyto informace se získávají z původní identifikátor URI zadaný uživatelem nebo odkazující prostředků (obecně adresu URL protokolu HTTP). V rozhraní .NET Framework verze 4, tyto informace můžete také nastavit klienta pomocí nového <xref:System.Net.HttpWebRequest.Host%2A> vlastnost.  
  
 <xref:System.Net.AuthenticationManager> Třídy řídí součásti spravované ověřování ("modules"), které jsou používány <xref:System.Net.WebRequest> odvozené třídy a <xref:System.Net.WebClient> třídy. <xref:System.Net.AuthenticationManager> Třída obsahuje vlastnosti, která zveřejňuje <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A?displayProperty=nameWithType> objekt indexovat pomocí řetězec identifikátoru URI, pro aplikace, které slouží k poskytování vlastní řetězec hlavního názvu služby používané během ověřování.  
  
 Exchange verze 3.5 SP1 nyní použity výchozí hodnoty se zadáním názvu hostitele v adrese URL požadavku v hlavní název služby v ověřování protokolem NTLM (NT LAN Manager), kdy <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A> není nastavena vlastnost. Název hostitele použitý v adrese URL požadavku se může lišit od zadané v záhlaví hostitele <xref:System.Net.HttpRequestHeader?displayProperty=nameWithType> v požadavku klienta. Název hostitele použitý v adrese URL požadavku se může lišit od skutečným názvem hostitele serveru, název počítače serveru, IP adresu počítače nebo na adresu zpětné smyčky. V těchto případech Windows selže požadavek na ověření. Chcete-li tento problém vyřešit, je třeba upozornit Windows, který používá název hostitele v adrese URL požadavku v klientovi požadavek ("contoso", například) je ve skutečnosti alternativní název pro místní počítač.  
  
 Existuje několik možných metod pro serverové aplikace, chcete-li tuto změnu. Doporučený postup je mapování názvu hostitele použít v adrese URL požadavku na `BackConnectionHostNames` klíče v registru na serveru. `BackConnectionHostNames` Klíč registru se obvykle používá k mapování názvu hostitele na adresu zpětné smyčky. Kroky jsou uvedeny níže.  
  
 Zadejte názvy hostitelů, které jsou mapovány na adresu zpětné smyčky a můžou se připojit k webovým stránkám na místním počítači, postupujte podle těchto kroků:  
  
 1. Klikněte na tlačítko Start, klikněte na spustit, zadejte regedit a pak klikněte na tlačítko OK.  
  
 2. V editoru registru vyhledejte a pak klikněte na následující klíč registru:  
  
 `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa\MSV1_0`  
  
 3. Klikněte pravým tlačítkem na MSV1_0, přejděte na nový a klikněte na Víceřetězcová hodnota.  
  
 4. Typ `BackConnectionHostNames`, a potom stiskněte klávesu ENTER.  
  
 5. Klikněte pravým tlačítkem na `BackConnectionHostNames`a potom klikněte na Upravit.  
  
 6. V poli Údaj hodnoty zadejte název hostitele nebo názvy hostitelů pro servery (název hostitele použitý v adrese URL žádosti), které jsou v místním počítači a potom klikněte na tlačítko OK.  
  
 7. Ukončete program Editor registru a potom restartujte službu IISAdmin a spusťte příkaz IISReset.  
  
 Méně bezpečné pracovní přibližně je zakázat kontroly zpětné smyčky, jak je popsáno v [ http://support.microsoft.com/kb/896861 ](https://go.microsoft.com/fwlink/?LinkID=179657). Zakáže ochranu před útoky na reflexi. Proto je lepší omezit sadu alternativní názvy pouze ty, které očekáváte, že počítač skutečně používáte.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A?displayProperty=nameWithType>  
 <xref:System.Net.HttpRequestHeader?displayProperty=nameWithType>  
 <xref:System.Net.HttpWebRequest.Host%2A?displayProperty=nameWithType>
