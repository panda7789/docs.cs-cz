---
title: Změny v ověřování NTLM pro HttpWebRequest ve verzi 3.5 SP1
ms.date: 03/30/2017
ms.assetid: 8bf0b428-5a21-4299-8d6e-bf8251fd978a
ms.openlocfilehash: 388e6dc648e1fd68e24a852cb08de107f09f9c9f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "64754874"
---
# <a name="changes-to-ntlm-authentication-for-httpwebrequest-in-version-35-sp1"></a>Změny v ověřování NTLM pro HttpWebRequest ve verzi 3.5 SP1

Změny zabezpečení byly provedeny v rozhraní .NET Framework verze 3.5 SP1 <xref:System.Net.HttpWebRequest>a <xref:System.Net.HttpListener> <xref:System.Net.Security.NegotiateStream>později, které ovlivňují způsob, jakým je integrované ověřování systému Windows zpracováno třídami , , a souvisejícími v oboru názvů System.Net. Tyto změny mohou ovlivnit aplikace, které používají tyto třídy k provádění webových požadavků a přijímání odpovědí, kde se používá integrované ověřování systému Windows založené na NTLM. Tato změna může mít vliv na webové servery a klientské aplikace, které jsou nakonfigurovány pro použití integrovaného ověřování systému Windows.

## <a name="overview"></a>Přehled

Návrh integrovaného ověřování systému Windows umožňuje, aby některé odpovědi na pověření byly univerzální, což znamená, že mohou být znovu použity nebo předány. Pokud tato konkrétní funkce návrhu není potřeba, měly by ověřovací protokoly obsahovat specifické informace o cíli a informace specifické pro kanál. Služby pak mohou poskytovat rozšířenou ochranu, aby bylo zajištěno, že odpovědi na pověření obsahují informace specifické pro službu, jako je například hlavní název služby (SPN). S těmito informacemi ve výměně pověření služby jsou schopny lépe chránit před škodlivým použitím odpovědi na pověření, které mohly být získány nesprávně.

Více součástí v <xref:System.Net> <xref:System.Net.Security> oborech názvů a provádění integrovaného ověřování systému Windows jménem volající aplikace. Tato část popisuje změny System.Net součástí pro přidání rozšířené ochrany při používání integrovaného ověřování systému Windows.

## <a name="changes"></a>Změny

Proces ověřování NTLM používaný při integrovaném ověřování systému Windows zahrnuje výzvu vydanou cílovým počítačem a odeslanou zpět do klientského počítače. Když počítač obdrží výzvu, kterou sám vygeneroval, ověření se nezdaří, pokud se nejedná o zpětné připojení smyčky (například adresa IPv4 127.0.0.1).

Při přístupu ke službě spuštěné na interním webovém serveru je `http://contoso/service` běžný `https://contoso/service`přístup ke službě pomocí adresy URL podobné nebo . Název "contoso" často není název počítače, ve kterém je služba nasazena. A <xref:System.Net> související obory názvů podporují použití souboru AD Lok, DNS, NetBIOS, souboru hostitelů místního počítače (například obvykle WINDOWS\system32\drivers\etc\hosts) nebo souboru lmhosts místního počítače (například obvykle WINDOWS\system32\drivers\etc\lmhosts) k překladu názvů adres. Název "contoso" je vyřešen tak, aby požadavky odeslané do "contoso" jsou odesílány do příslušného počítače serveru.

Při konfiguraci pro velká nasazení je také běžné, že jeden název virtuálního serveru bude přidělen nasazení s podkladovými názvy počítačů, které klientské aplikace a koncoví uživatelé nikdy nepoužívali. Můžete například volat server `www.contoso.com`, ale v interní síti jednoduše použijte "contoso". Tento název se nazývá hlavička Hostitele ve webovém požadavku klienta. Jak je určeno protokolem HTTP, pole hlavička požadavku hostitele určuje číslo internetového hostitele a portu požadovaného prostředku. Tyto informace jsou získány z původního identifikátoru URI daného uživatelem nebo odkazujícího prostředku (obecně adresy URL HTTP). V rozhraní .NET Framework verze 4 mohou být tyto <xref:System.Net.HttpWebRequest.Host%2A> informace také nastaveny klientem pomocí nové vlastnosti.

Třída <xref:System.Net.AuthenticationManager> řídí spravované součásti ověřování ("moduly"), které <xref:System.Net.WebRequest> jsou používány odvozenými třídami a třídou. <xref:System.Net.WebClient> Třída <xref:System.Net.AuthenticationManager> poskytuje vlastnost, která <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A?displayProperty=nameWithType> zveřejňuje objekt indexovaný řetězcem URI, pro aplikace, které poskytují vlastní řetězec SPN, který má být použit při ověřování.

Verze 3.5 SP1 nyní ve výchozím nastavení určuje název hostitele použitý v adrese URL požadavku v názvu NÁZVU <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A> V ověřovací výměně NTLM (NT LAN Manager), pokud není vlastnost nastavena. Název hostitele použitý v adrese URL požadavku se může <xref:System.Net.HttpRequestHeader?displayProperty=nameWithType> lišit od hlavičky hostitele zadané v požadavku klienta. Název hostitele použitý v adrese URL požadavku se může lišit od skutečného názvu hostitele serveru, názvu počítače serveru, ip adresy počítače nebo adresy zpětné smyčky. V těchto případech systém Windows nezdaří požadavek na ověření. Chcete-li tento problém vyřešit, musíme upozornit systém Windows, že název hostitele použitý v adrese URL požadavku v požadavku klienta ("contoso", například) je ve skutečnosti alternativní název pro místní počítač.

Existuje několik možných metod pro serverové aplikace obejít tuto změnu. Doporučeným přístupem je mapování názvu hostitele použitého `BackConnectionHostNames` v adrese URL požadavku na klíč v registru na serveru. Klíč `BackConnectionHostNames` registru se obvykle používá k mapování názvu hostitele na adresu zpětné smyčky. Kroky jsou uvedeny níže.

Chcete-li určit názvy hostitelů, které jsou mapovány na adresu zpětné smyčky a mohou se připojit k webovým serverům v místním počítači, postupujte takto:

1. Klikněte na Start, klikněte na Spustit, zadejte regedit a pak klikněte na OK.

2. V Editoru registru vyhledejte následující klíč registru a klepněte na něj:

    `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa\MSV1_0`

3. Klikněte pravým tlačítkem myši na MSV1_0, přejděte na Nový a potom klikněte na Hodnotu více řetězců.

4. Zadejte `BackConnectionHostNames` a pak stiskněte ENTER.

5. Klepněte `BackConnectionHostNames`pravým tlačítkem myši a potom klepněte na příkaz Změnit.

6. Do datového pole Hodnota zadejte název hostitele nebo názvy hostitelů pro weby (název hostitele použitý v adrese URL požadavku), které jsou v místním počítači, a klepněte na tlačítko OK.

7. Ukončete Editor registru a restartujte službu IISAdmin a spusťte program IISReset.

Méně bezpečné řešení je zakázat zpětné kontroly smyčky, jak je popsáno v <https://support.microsoft.com/kb/896861>. Tím zakážete ochranu proti odrazu útoky. Proto je lepší omezit sadu alternativních názvů pouze na ty, které očekáváte, že počítač skutečně použít.

## <a name="see-also"></a>Viz také

- <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A?displayProperty=nameWithType>
- <xref:System.Net.HttpRequestHeader?displayProperty=nameWithType>
- <xref:System.Net.HttpWebRequest.Host%2A?displayProperty=nameWithType>
