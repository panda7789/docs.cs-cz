---
title: Konfigurace HTTP a HTTPS
description: Naučte se konfigurovat HTTP/HTTPS, aby mohly komunikovat služby a klienty WCF. Nakonfigurujte registraci adresy URL a výjimku brány firewall pomocí Netsh.exe.
ms.date: 04/08/2019
helpviewer_keywords:
- configuring HTTP [WCF]
ms.assetid: b0c29a86-bc0c-41b3-bc1e-4eb5bb5714d4
ms.openlocfilehash: fbff78ff8e2c5c4fa73a56a3fdc15163596aa985
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245138"
---
# <a name="configuring-http-and-https"></a>Konfigurace HTTP a HTTPS

Služby a Klienti WCF můžou komunikovat přes protokol HTTP a HTTPS. Nastavení HTTP/HTTPS jsou nakonfigurovaná pomocí Internetová informační služba (IIS) nebo pomocí nástroje příkazového řádku. Když je služba WCF hostovaná v rámci nastavení IIS HTTP nebo HTTPS, můžete nakonfigurovat v rámci služby IIS (pomocí nástroje inetmgr.exe). Pokud je služba WCF v místním prostředí, nastavení HTTP nebo HTTPS se konfigurují pomocí nástroje příkazového řádku.

Minimálně je potřeba nakonfigurovat registraci adresy URL a přidat výjimku brány firewall pro adresu URL, kterou bude služba používat. Tato nastavení můžete nakonfigurovat pomocí nástroje Netsh.exe.

## <a name="configuring-namespace-reservations"></a>Konfigurace rezervací oboru názvů

Rezervace oboru názvů přiřadí práva pro část oboru názvů URL protokolu HTTP ke konkrétní skupině uživatelů. Rezervace dává těmto uživatelům právo vytvářet služby, které naslouchají této části oboru názvů. Rezervace jsou předpony adres URL, což znamená, že rezervace pokrývá všechny dílčí cesty cesty rezervace. Rezervace oboru názvů povolují dva způsoby použití zástupných znaků. Dokumentace k rozhraní API serveru HTTP popisuje [pořadí rozlišení mezi deklaracemi oboru názvů, které zahrnují zástupné znaky](/windows/desktop/Http/routing-incoming-requests).

Běžící aplikace může vytvořit podobný požadavek na přidání registrace oboru názvů. Registrace a rezervace jsou konkurenční pro části oboru názvů. Rezervace může mít přednost před registrací podle pořadí rozlišení [mezi deklaracemi oboru názvů, které zahrnují zástupné znaky](/windows/desktop/Http/routing-incoming-requests). V takovém případě rezervace blokuje běžící aplikaci od přijímání požadavků.

Následující příklad používá nástroj Netsh.exe:

```console
netsh http add urlacl url=http://+:80/MyUri user=DOMAIN\user
```

Tento příkaz přidá rezervaci adresy URL pro zadaný obor názvů URL pro účet doména \ uživatel. Další informace o použití příkazu netsh získáte zadáním `netsh http add urlacl /?` příkazu do příkazového řádku a stisknutím klávesy ENTER.

## <a name="configuring-a-firewall-exception"></a>Konfigurace výjimky brány firewall

Při samoobslužném hostování služby WCF, která komunikuje přes protokol HTTP, musí být do konfigurace brány firewall přidána výjimka umožňující příchozí připojení pomocí konkrétní adresy URL.

## <a name="configuring-ssl-certificates"></a>Konfigurace certifikátů SSL

Protokol SSL (SSL (Secure Sockets Layer)) používá k ukládání šifrovacích klíčů certifikáty na klientovi a na serveru. Server poskytuje svůj certifikát SSL, když je vytvořeno připojení, aby klient mohl ověřit identitu serveru. Server taky může požádat o certifikát od klienta, aby se zajistilo vzájemné ověřování obou stran připojení.

Certifikáty jsou uložené v centralizovaném úložišti podle IP adresy a čísla portu připojení. Speciální IP adresa 0.0.0.0 odpovídá libovolné IP adrese pro místní počítač. Všimněte si, že úložiště certifikátů nerozlišuje adresy URL na základě cesty. Služby se stejnou kombinací IP adresy a portu musí sdílet certifikáty, i když je cesta v adrese URL pro služby odlišná.

Podrobné pokyny najdete v tématu [Postup: Konfigurace portu s certifikátem SSL](how-to-configure-a-port-with-an-ssl-certificate.md).

## <a name="configuring-the-ip-listen-list"></a>Konfigurace seznamu naslouchání protokolu IP

Rozhraní API serveru HTTP se váže jenom na IP adresu a port, jakmile uživatel zaregistruje adresu URL. Rozhraní API serveru HTTP se ve výchozím nastavení váže k portu v adrese URL pro všechny IP adresy daného počítače. Konflikt nastane, pokud aplikace, která nepoužívá rozhraní API serveru HTTP, byla dříve vázaná na tuto kombinaci IP adresy a portu. Seznam naslouchání protokolu IP umožňuje službám WCF koexistovat s aplikacemi, které používají port pro některé z IP adres počítače. Pokud seznam naslouchání protokolu IP obsahuje nějaké položky, rozhraní API serveru HTTP se váže pouze na tyto IP adresy, které seznam určuje. Změna seznamu naslouchání protokolu IP vyžaduje oprávnění správce.

Pomocí nástroje Netsh upravte seznam IP listeny, jak je znázorněno v následujícím příkladu:

```console
netsh http add iplisten ipaddress=0.0.0.0:8000
```

## <a name="other-configuration-settings"></a>Další nastavení konfigurace

Při použití nástroje <xref:System.ServiceModel.WSDualHttpBinding> připojení klienta používá výchozí hodnoty, které jsou kompatibilní s rezervacemi oboru názvů a bránou Windows Firewall. Pokud se rozhodnete přizpůsobit základní adresu klienta duálního připojení, musíte také nakonfigurovat tato nastavení protokolu HTTP v klientovi tak, aby odpovídala nové adrese.

Rozhraní API serveru HTTP má několik pokročilých nastavení konfigurace, která nejsou k dispozici prostřednictvím HttpCfg. Tato nastavení jsou zachována v registru a platí pro všechny aplikace spuštěné v systémech, které používají rozhraní API serveru HTTP. Informace o těchto nastaveních najdete v tématu [Http.sys nastavení registru pro službu IIS](https://support.microsoft.com/help/820129/http-sys-registry-settings-for-windows). Většina uživatelů tyto nastavení nepotřebuje měnit.

## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.WSDualHttpBinding>
- [Postupy: Konfigurace portu s certifikátem SSL](how-to-configure-a-port-with-an-ssl-certificate.md)
