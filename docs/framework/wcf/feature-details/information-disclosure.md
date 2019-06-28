---
title: Zpřístupnění informací
ms.date: 03/30/2017
ms.assetid: 4064c89f-afa6-444a-aa7e-807ef072131c
ms.openlocfilehash: 0e45a71855ecb172f36aae8139f89d4b8c8ffd0d
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2019
ms.locfileid: "67425311"
---
# <a name="information-disclosure"></a>Zpřístupnění informací

Zpřístupnění informací umožňuje útočníkovi získat cenné informace o systému. Proto vždy zvažte, jaké informace jsou odhalení a určuje, zda je možné uživatele se zlými úmysly. Následující informace o možných útoků zpřístupnění obsahuje seznam a způsoby zmírnění rizik pro každý.

## <a name="message-security-and-http"></a>Zabezpečení zpráv a HTTP

Pokud používáte zabezpečení na úrovni zprávy v přenosové vrstvě HTTP, mějte na paměti, že zabezpečení na úrovni zprávy nechrání hlavičky protokolu HTTP. Jediný způsob, jak chránit hlavičky protokolu HTTP je použití přenos protokolu HTTPS místo protokolu HTTP. Přenos protokolu HTTPS způsobí, že celá zpráva, včetně hlavičky protokolu HTTP k šifrování pomocí protokolu vrstvy SSL (Secure Sockets).

## <a name="policy-information"></a>Informace o zásadách

Zásady zabezpečení je důležité, zejména ve scénářích s federací kde citlivé token vystavený požadavky nebo informace o vydavateli token vystavený v zásadách. V těchto případech doporučujeme k zabezpečení koncového bodu služby federované zásady bránící útočníkům v získání informací o službě, jako je typ deklarace identity se umístí vydaný token, nebo přesměrovat klienty na škodlivý vystavitele tokenu. Útočník může například zjistit párů jméno/heslo uživatele překonfigurováním řetězu federovaný vztah důvěryhodnosti k ukončení v vystavitele, který proveden útok man-in-the-middle. Doporučujeme také federované klienty, kteří získat jejich vazby prostřednictvím načtení zásad ověřte, zda důvěřují vystavitele v řetězu získaného federovaný vztah důvěryhodnosti. Další informace o scénářích s federací, naleznete v tématu [federace](../../../../docs/framework/wcf/feature-details/federation.md).

## <a name="memory-dumps-can-reveal-claim-information"></a>Výpisy paměti můžete zobrazit informace o deklaraci identity

Pokud aplikace selže, protokolovat soubory, jako jsou ty vytvářených zotavení po havárii. Watson, může obsahovat informace o deklaraci identity. Tyto informace nesmí exportovat do jiné entity, jako je například týmy podpory; v opačném případě se exportují také informace o deklaraci identity, která obsahuje osobní data. Tento problém můžete zmírnit odesláním souborů protokolu na neznámý entity. Další informace najdete v tématu [systému Windows Server 2003](https://go.microsoft.com/fwlink/?LinkId=89160).

## <a name="endpoint-addresses"></a>Adresy koncových bodů

Adresy koncového bodu obsahuje informace potřebné ke komunikaci s koncovým bodem. Zabezpečení protokolu SOAP musí obsahovat adresu plně ve zprávách vyjednávání zabezpečení, které se vyměňují, aby bylo možné vyjednávání symetrického klíče mezi klientem a serverem. Protože vyjednávání zabezpečení je spuštění procesu, záhlaví adres nelze zašifrovat během tohoto procesu. Proto adresa nesmí obsahovat jakákoli důvěrná data, v opačném případě vede k útokům zpřístupnění informací.

## <a name="certificates-transferred-unencrypted"></a>Přenést nešifrované certifikáty

Pokud certifikát X.509, který použijete k ověření klienta, certifikát se přenesou v nezašifrované podobě, v záhlaví SOAP. Mějte na paměti tohoto jako potenciální zpřístupnění identifikovatelné osobní údaje (PII). To není problém pro `TransportWithMessageCredential` režimu, kde je zašifrovaná celá zpráva se zabezpečením na úrovni přenosu.

## <a name="service-references"></a>Odkazy na služby

Odkaz na službu je odkazem na jinou službu. Služba může například předat odkaz na službu klienta v průběhu operace. Odkaz na službu se také používá s *důvěřovat ověřovatele identity*, vnitřní komponenta, která zajišťuje identita cílového objektu zabezpečení před zveřejnění informací o jako data aplikací nebo přihlašovací údaje k cíli. Pokud vzdálené důvěryhodnosti identity nelze ověřit nebo není správná, odesílatel zajistil, že žádná data byl zveřejněn, které by mohly ohrozit samotné, aplikaci nebo uživatele.

Zmírnění rizik, patří:

- Odkazy na služby, jsou považovány za důvěryhodné. Je třeba dbát pokaždé, když se přenos odkaz instance služby k zajištění, že nebylo manipulováno.

- Některé aplikace mohou představovat uživatelské prostředí, která umožňuje interaktivní navázání vztahu důvěryhodnosti na základě dat v odkazu a důvěryhodnost data služby ověřené vzdáleným hostitelem. WCF poskytuje body rozšiřitelnosti pro taková zařízení, ale uživatel je musí implementovat.

## <a name="ntlm"></a>NTLM

Ve výchozím nastavení v prostředí domény Windows, Windows ověřování používá protokol Kerberos k ověřování a autorizaci uživatelů. Pokud z nějakého důvodu nelze použít protokol Kerberos, NT LAN Manager (NTLM) se používá jako záložní. Toto chování lze zakázat nastavením <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> vlastnost `false`. Problémy, které je potřeba při povolení protokolu NTLM patří:

- NTLM zpřístupňuje klientské uživatelské jméno. Pokud uživatelské jméno musí být důvěrný, nastavte `AllowNTLM` vlastnost pro vazbu k `false`.

- NTLM neposkytuje ověřování serveru. Klient nemůže proto ujistěte se, že při použití jako ověřovací protokol NTLM, to je nekomunikují s požadovanou službu.

### <a name="specifying-client-credentials-or-invalid-identity-forces-ntlm-usage"></a>Zadání přihlašovacích údajů klienta nebo neplatná identita vynutí používání protokolu NTLM

Při vytváření klienta, když zadáváte přihlašovací údaje klienta bez názvu domény nebo určení identity serveru je neplatný, způsobí, že protokolu NTLM namísto protokolu Kerberos použita (Pokud `AllowNtlm` je nastavena na `true`). Protože protokol NTLM neprovádí ověřování serveru, může být odhalena potenciálně informace.

Například je možné zadat přihlašovací údaje pro klienta Windows bez názvu domény, jak je znázorněno v následujícím kódu jazyka Visual C#.

```csharp
MyChannelFactory.Credentials.Windows.ClientCredential = new System.Net.NetworkCredential("username", "password");
```

Kód neurčuje název domény, a proto se použije protokol NTLM.

Pokud je zadané doméně, ale na neplatný hlavní název služby je určen pomocí funkce identity koncový bod, je použit protokol NTLM. Další informace o tom, jak je zadána identitě koncového bodu najdete v tématu [identita a ověřování služby](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).

## <a name="see-also"></a>Viz také:

- [Důležité informace o zabezpečení](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)
- [Zvýšení oprávnění](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)
- [Útok DoS](../../../../docs/framework/wcf/feature-details/denial-of-service.md)
- [Falšování](../../../../docs/framework/wcf/feature-details/tampering.md)
- [Nepodporované scénáře](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
- [Útoky opakováním](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
