---
title: Zásady rozšířené ochrany
ms.date: 03/30/2017
ms.assetid: e2616a10-317e-4c34-8023-0c015a80a82f
ms.openlocfilehash: 3a5b1c7f296c68d407f0217963dec56f53e9a08a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144719"
---
# <a name="extended-protection-policy"></a>Zásady rozšířené ochrany
Rozšířená ochrana je bezpečnostní iniciativa pro ochranu proti útokům man-in-the-middle (MITM). Útok MITM je bezpečnostní hrozba, při které MITM přebírá pověření klienta a předá je serveru.  
  
## <a name="demonstrates"></a>Demonstruje  
 Rozšířená ochrana  
  
## <a name="discussion"></a>Diskuse  
 Při ověřování aplikací pomocí protokolu Kerberos, Digest nebo NTLM pomocí protokolu HTTPS je nejprve vytvořen kanál TLS (Transport Level Security) a ověřování probíhá pomocí zabezpečeného kanálu. Neexistuje však žádná vazba mezi klíčem relace generovaným protokolem SSL a klíčem relace generovaným během ověřování. Libovolný MITM může etablovat mezi klientem a serverem a začít předávat požadavky z klienta, i když přenosový kanál sám je bezpečný, protože server nemá žádný způsob, jak zjistit, zda byl vytvořen zabezpečený kanál z klienta nebo MITM. Řešení v tomto scénáři je vázat vnější kanál TLS s kanálem vnitřní ověřování tak, aby server může zjistit, zda je MITM.  
  
> [!NOTE]
> Tato ukázka funguje pouze při hostování ve službě IIS a nemůže pracovat na Cassini – Visual Studio Development Server, protože Cassini nepodporuje protokol HTTPS.  
  
> [!NOTE]
> Tato funkce je v současné době k dispozici pouze v systému Windows 7. Následující kroky jsou specifické pro systém Windows 7.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Instalace Internetové informační služby z **Ovládacích panelů**, **Přidat nebo odebrat programy**, Funkce **systému Windows**.  
  
2. Instalace **ověřování systému Windows** v **funkcích systému Windows**, Internetové informační **službě**, **službách World Wide Web Services**, **zabezpečení**a **ověřování systému Windows**.  
  
3. Instalace **aktivace protokolu HTTP nadace Windows Communication Foundation** v **funkcích systému Windows**, rozhraní Microsoft **.NET Framework 3.5.1**a **aktivace protokolu HTTP organizace Windows Communication Foundation**.  
  
4. Tato ukázka vyžaduje, aby klient vytvořil se serverem zabezpečený kanál, takže vyžaduje přítomnost certifikátu serveru, který lze nainstalovat ze Správce Internetové informační služby (IIS).  
  
    1. Spusťte Správce služby IIS. Otevřete **certifikáty serveru**, které se zobrazí na kartě **Zobrazení funkcí,** když je vybrán kořenový uzel (název počítače).  
  
    2. Pro účely testování této ukázky vytvořte certifikát podepsaný svým držitelem. Pokud nechcete, aby vás aplikace Internet Explorer zobrazovala s výzvou k nezabezpečeníu certifikátu, nainstalujte jej do úložiště kořenových certifikátů.  
  
5. Otevřete podokno **Akce** pro výchozí web. Klepněte na **položku Upravit web**, **Vazby**. Přidejte https jako typ, pokud již není k dispozici, s portem číslo 443. Přiřaďte certifikát SSL vytvořený v předchozím kroku.  
  
6. Sestavte službu. Tím se vytvoří virtuální adresář ve službě IIS a zkopíruje soubory DLL, SVC a .config podle potřeby pro hostování služby na webu.  
  
7. Spusťte Správce služby IIS. Klepněte pravým tlačítkem myši na virtuální adresář (**ExtendedProtection**), který byl vytvořen v předchozím kroku. Vyberte **Převést na aplikaci**.  
  
8. Otevřete modul **Ověřování** ve Správci služby IIS pro tento virtuální adresář a povolte **ověřování systému Windows**.  
  
9. V **Advanced Settings** části Ověřování systému Windows v části **Ověřování systému systému** otevřete v části Ověřování **systému Windows**a nastavte jej na povinné .  
  
10. Službu můžete otestovat přístupem k adrese URL HTTPS z okna prohlížeče (Zadejte plně kvalifikovaný název domény). Pokud chcete získat přístup k této adrese URL ze vzdáleného počítače, zkontrolujte, zda je brána firewall otevřena pro všechna příchozí připojení HTTP a HTTPS.  
  
11. Otevřete konfigurační soubor klienta a zadejte plně kvalifikovaný název `<<full_machine_name>>`domény pro atribut adresy klienta nebo koncového bodu, který nahrazuje .  
  
12. Spusťte klienta. Klient komunikuje se službou, která vytváří zabezpečený kanál a používá rozšířenou ochranu.  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Security\ExtendedProtection`
