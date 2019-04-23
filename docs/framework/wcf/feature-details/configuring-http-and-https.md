---
title: Konfigurace HTTP a HTTPS - WCF
ms.date: 04/08/2019
helpviewer_keywords:
- configuring HTTP [WCF]
ms.assetid: b0c29a86-bc0c-41b3-bc1e-4eb5bb5714d4
ms.openlocfilehash: 86705a4f8daa327c442ac6c53c9b44c5b5c5c2ad
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59427172"
---
# <a name="configuring-http-and-https"></a>Konfigurace HTTP a HTTPS

Služby WCF a klienti mohou komunikovat prostřednictvím protokolu HTTP a HTTPS. Nastavení HTTP/HTTPS se konfigurují pomocí Internetové informační služby (IIS) nebo pomocí nástroje příkazového řádku. Když je služba WCF hostované na nastavení služby IIS protokolu HTTP nebo HTTPS lze nastavit v rámci služby IIS (pomocí nástroje inetmgr.exe). Pokud je služba WCF v místním prostředí, HTTP nebo HTTPS je nakonfigurováno pomocí nástroje příkazového řádku.

Minimálně chcete konfigurovat adresu URL registrace a přidat výjimku brány Firewall pro adresu URL vaší služby budete používat. Tato nastavení můžete konfigurovat pomocí nástroje Netsh.exe.

## <a name="configuring-namespace-reservations"></a>Konfigurace rezervace oboru názvů

Rezervace Namespace přiřadí oprávnění pro část oboru názvů HTTP URL ke konkrétní skupině uživatelů. Rezervace opravňuje tito uživatelé vytvářet služby, které naslouchat na část oboru názvů. Rezervace se předpony adres URL, to znamená, že rezervace pokrývá všechny dílčí cesty rezervace. Rezervace Namespace povolit dva způsoby, jak použít zástupné znaky. Popisuje dokumentace k rozhraní API serveru HTTP [pořadí rozlišení rozsahu deklarace identity oboru názvů, které se týkají zástupné znaky](/windows/desktop/Http/routing-incoming-requests).

Podobně jako požadavek na přidání registrace oboru názvů můžete vytvořit běžící aplikaci. Registrace a rezervace soutěžit o části obor názvů. Rezervace mohou mít přednost před registrace podle pořadí podle rozlišení [pořadí rozlišení rozsahu deklarace identity oboru názvů, které se týkají zástupné znaky](/windows/desktop/Http/routing-incoming-requests). V takovém případě rezervace blokuje běžící aplikaci příjem požadavků.

Pomocí nástroje Netsh.exe v následujícím příkladu:

```console
netsh http add urlacl url=http://+:80/MyUri user=DOMAIN\user
```

Tento příkaz přidá rezervaci adresy URL pro obor názvů zadané adresy URL pro účet doména\uživatel. Další informace o použití příkazu netsh, zadejte `netsh http add urlacl /?` v příkazovém řádku a potom stiskněte klávesu Enter.

## <a name="configuring-a-firewall-exception"></a>Konfigurace výjimek brány firewall

Při samoobslužné hostování služby WCF, který komunikuje přes protokol HTTP, výjimky musí být přidány do konfigurace brány firewall pro povolení příchozích připojení pomocí konkrétní adresy URL.

## <a name="configuring-ssl-certificates"></a>Konfigurace certifikátů SSL

Protokol vrstvy SSL (Secure Sockets) používá certifikáty na klienta a serveru pro ukládání šifrovacích klíčů. Server poskytuje svůj certifikát SSL, když se vytvoří připojení tak, aby klient lze ověřit identitu serveru. Na serveru můžete také požádat o certifikát od klienta k zajištění vzájemného ověřování obou stranách připojení.

Certifikáty jsou uloženy v centralizované úložiště podle IP adresy a portu počtu připojení. Speciální IP adresu 0.0.0.0 odpovídá jakékoli IP adresu místního počítače. Všimněte si, že úložiště certifikátů není rozlišit adresy URL na základě cesty. Služby se stejnou IP adresu a port kombinací musí sdílet certifikáty, i v případě, že cesta v adrese URL pro služby se liší.

Podrobné pokyny najdete v tématu [jak: Konfigurace portu s certifikátem SSL](how-to-configure-a-port-with-an-ssl-certificate.md).

## <a name="configuring-the-ip-listen-list"></a>Konfigurace seznamu vlastností listenurimode nastavenou IP

Rozhraní API HTTP serveru vytvoří vazbu jenom na IP adresu a port jakmile se uživatel zaregistruje adresy URL. Ve výchozím nastavení rozhraní API serveru HTTP váže na port v adrese URL pro všechny IP adresy počítače. Konflikt nastane, pokud aplikace, která nepoužívá rozhraní API serveru HTTP byl dříve spojen daná kombinace IP adresy a portu. Seznam naslouchání IP umožňuje služeb WCF pro existovat současně s aplikací, které používají port pro některé z IP adresy počítače. Pokud IP naslouchání seznam obsahuje všechny položky, rozhraní API HTTP serveru pouze vytvoří vazbu tyto IP adresy, které určuje seznamu. Úprava seznamu naslouchání IP vyžaduje oprávnění správce.

Pomocí nástroje netsh k úpravě seznamu naslouchání IP, jak je znázorněno v následujícím příkladu:

```console
netsh http add iplisten ipaddress=0.0.0.0:8000
```

## <a name="other-configuration-settings"></a>Další nastavení konfigurace

Při použití <xref:System.ServiceModel.WSDualHttpBinding>, připojení klienta používá výchozí hodnoty, které jsou kompatibilní s rezervace oboru názvů a brány Windows firewall. Pokud budete chtít upravit základní adresu duální připojení klienta, také musíte nakonfigurovat nastavení protokolu HTTP na straně klienta tak, aby odpovídala nové adrese.

Rozhraní API HTTP Server má nastavení některé pokročilé konfigurace, které nejsou k dispozici prostřednictvím HttpCfg. Tato nastavení se zachovají v registru a platí pro všechny aplikace spuštěné v systémech, které používají rozhraní API serveru HTTP. Informace o těchto nastaveních najdete v tématu [nastavení registru Http.sys pro službu IIS](https://support.microsoft.com/en-us/help/820129/http-sys-registry-settings-for-windows). Většina uživatelů nemusí tato nastavení změnit.

## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.WSDualHttpBinding>
- [Postupy: Konfigurace portu s certifikátem SSL](how-to-configure-a-port-with-an-ssl-certificate.md)
