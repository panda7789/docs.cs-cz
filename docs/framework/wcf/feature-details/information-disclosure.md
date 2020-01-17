---
title: Zpřístupnění informací
ms.date: 03/30/2017
ms.assetid: 4064c89f-afa6-444a-aa7e-807ef072131c
ms.openlocfilehash: 0bcf1aa04d7ba7477a6c3f1559a77bbda1f974af
ms.sourcegitcommit: 09b4090b78f52fd09b0e430cd4b26576f1fdf96e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2020
ms.locfileid: "76211947"
---
# <a name="information-disclosure"></a>Zpřístupnění informací

Zpřístupnění informací umožňuje útočníkovi získat cenné informace o systému. Proto vždy Vezměte v úvahu, jaké informace se vám odhalí a jestli je může používat uživatel se zlými úmysly. V následující části jsou uvedeny možné útoky na zpřístupnění informací a pro každou z nich jsou k dispozici rizika.

## <a name="message-security-and-http"></a>Zabezpečení zpráv a HTTP

Pokud používáte zabezpečení na úrovni zprávy přes transportní vrstvu HTTP, pamatujte, že zabezpečení na úrovni zpráv nechrání hlavičky protokolu HTTP. Jediným způsobem, jak chránit hlavičky protokolu HTTP, je použít přenos HTTPS místo HTTP. Přenos HTTPS způsobuje šifrování celé zprávy včetně hlaviček protokolu HTTP pomocí protokolu SSL (Secure Sockets Layer) (SSL).

## <a name="policy-information"></a>Informace o zásadách

Zachování zabezpečení zásad je důležité, zejména ve federačních scénářích, ve kterých se v zásadách zveřejňují citlivé požadavky na vydané tokeny nebo informace vystavitele tokenů. V těchto případech doporučujeme zajistit zabezpečení koncového bodu zásad federovaného služby a zabránit tak útočníkům v získání informací o službě, jako je například typ deklarací identity, které mají být vloženy do vydaného tokenu, nebo přesměrování klientů na škodlivé vydavatele tokenů. Útočník by například mohl zjistit páry uživatelského jména a hesla tím, že znovu nakonfiguruje federovaný řetěz důvěryhodnosti tak, aby ukončil vystavitele, který provedl útok prostředníkem. Také se doporučuje, aby federované klienty, kteří získají své vazby prostřednictvím načtení zásad, ověřili, že důvěřují vystavitelům v získaném federovaném řetězu důvěryhodných certifikátů. Další informace o federačních scénářích najdete v tématu [federace](../../../../docs/framework/wcf/feature-details/federation.md).

## <a name="memory-dumps-can-reveal-claim-information"></a>Výpisy paměti můžou odhalit informace o deklaraci identity.

Pokud dojde k chybě aplikace, můžou soubory protokolu, například ty, které vytvořil program Dr. Watson, obsahovat informace o deklaraci identity. Tyto informace by se neměly exportovat do jiných entit, jako jsou například týmy podpory. v opačném případě jsou exportovány také informace o deklaraci identity, které obsahují soukromá data. To můžete zmírnit tím, že soubory protokolu neposíláte neznámým entitám.

## <a name="endpoint-addresses"></a>Adresy koncových bodů

Adresa koncového bodu obsahuje informace potřebné ke komunikaci s koncovým bodem. Zabezpečení SOAP musí obsahovat adresu v plném rozsahu ve zprávách vyjednávání zabezpečení, které se vyměňují, aby vyjednaly symetrický klíč mezi klientem a serverem. Vzhledem k tomu, že vyjednávání zabezpečení je proces Bootstrap, hlavičky adres nelze během tohoto procesu šifrovat. Adresa by proto neměla obsahovat žádná důvěrné data; v opačném případě vede k útokům prostřednictvím odhalení informací.

## <a name="certificates-transferred-unencrypted"></a>Přenesené certifikáty nejsou šifrované

Když k ověření klienta použijete certifikát X. 509, certifikát se přenese v nešifrovaném formátu v hlavičce SOAP. Uvědomte si to jako potenciální zpřístupnění identifikovatelných osobních údajů (PII). Nejedná se o problém s režimem `TransportWithMessageCredential`, kde je celá zpráva zašifrovaná pomocí zabezpečení na úrovni přenosu.

## <a name="service-references"></a>Odkazy na služby

Odkaz na službu je odkaz na jinou službu. Služba může například předat odkaz na službu klientovi v průběhu operace. Odkaz na službu se používá také společně s *ověřovatelem identity identity*, interní komponenta, která zajišťuje identitu cílového objektu zabezpečení před tím, než jsou v cíli využívány informace, jako jsou data aplikace nebo přihlašovací údaje. Pokud se identita vzdáleného vztahu důvěryhodnosti nedá ověřit nebo je nesprávná, odesílatel by měl zajistit, aby žádná data nebyla zveřejněná, která by mohla ohrozit samotnou aplikaci nebo uživatele.

Zmírnění rizik zahrnuje následující:

- Odkazy na službu se považují za důvěryhodné. Při přenosu instancí odkazů na službu se ujistěte, že nejsou úmyslně poškozeny.

- Některé aplikace mohou představovat uživatelské prostředí, které umožňuje interaktivní zřízení vztahu důvěryhodnosti na základě dat v odkazu na službu a vztahu důvěryhodnosti ověřených vzdáleným hostitelem. WCF poskytuje body rozšiřitelnosti pro takové zařízení, ale uživatel je musí implementovat.

## <a name="ntlm"></a>NTLM

Ve výchozím nastavení používá ověřování systému Windows v prostředí domény Windows k ověřování a autorizaci uživatelů protokol Kerberos. Pokud protokol Kerberos z nějakého důvodu nemůžete použít, použije se jako záložní program NT LAN Manager (NTLM). Toto chování můžete zakázat nastavením vlastnosti <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> na `false`. Mezi problémy, které je potřeba vědět při povolování protokolu NTLM, patří:

- Protokol NTLM zveřejňuje uživatelské jméno klienta. Pokud se uživatelské jméno musí uchovávat jako důvěrné, nastavte vlastnost `AllowNTLM` vazby na `false`.

- Protokol NTLM neposkytuje ověřování serveru. Proto klient nemůže zajistit, aby při použití protokolu NTLM jako ověřovacího protokolu komunikoval se správnou službou.

### <a name="specifying-client-credentials-or-invalid-identity-forces-ntlm-usage"></a>Zadání přihlašovacích údajů klienta nebo neplatné identity vynutí použití protokolu NTLM

Při vytváření klienta, zadání přihlašovacích údajů klienta bez názvu domény nebo zadání neplatné identity serveru způsobí, že se protokol NTLM použije místo protokolu Kerberos (Pokud je vlastnost `AllowNtlm` nastavená na `true`). Vzhledem k tomu, že protokol NTLM neprovádí ověřování serveru, mohou být informace potenciálně zveřejněny.

Například je možné zadat přihlašovací údaje klienta Windows bez názvu domény, jak je znázorněno v následujícím kódu vizuálu C# .

```csharp
MyChannelFactory.Credentials.Windows.ClientCredential = new System.Net.NetworkCredential("username", "password");
```

Kód neurčuje název domény, a proto bude použit protokol NTLM.

Pokud je zadaná doména, ale pomocí funkce identity koncového bodu je zadaný neplatný hlavní název služby, pak se použije NTLM. Další informace o tom, jak se určuje identita koncového bodu, najdete v tématu [Identita a ověřování služby](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).

## <a name="see-also"></a>Viz také:

- [Důležité informace o zabezpečení](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)
- [Zvýšení oprávnění](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)
- [Útok DoS](../../../../docs/framework/wcf/feature-details/denial-of-service.md)
- [Falšování](../../../../docs/framework/wcf/feature-details/tampering.md)
- [Nepodporované scénáře](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
- [Útoky opakováním](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
