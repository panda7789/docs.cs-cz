---
title: Zásady rozšířené ochrany
ms.date: 03/30/2017
ms.assetid: e2616a10-317e-4c34-8023-0c015a80a82f
ms.openlocfilehash: 1cb6d44e8f6ee8f54f776453e5a1783ab0cfa4f0
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716427"
---
# <a name="extended-protection-policy"></a>Zásady rozšířené ochrany
Rozšířená ochrana je bezpečnostní iniciativa pro ochranu proti útokům MITM (man-in-the-middle). Útok MITM je bezpečnostní hrozba, ve které MITM přebírá přihlašovací údaje klienta a předává je na server.  
  
## <a name="demonstrates"></a>Demonstruje  
 Rozšířená ochrana  
  
## <a name="discussion"></a>Účely  
 Když se aplikace ověřují pomocí protokolu Kerberos, Digest nebo NTLM pomocí protokolu HTTPS, nejprve se vytvoří kanál TLS (Transport Level Security) a pak proběhne ověřování pomocí zabezpečeného kanálu. Neexistuje ale žádná vazba mezi klíčem relace generovaným protokolem SSL a klíčem relace generovaným při ověřování. Všechny MITM se můžou navázat mezi klientem a serverem a začít předávat požadavky z klienta, i když je transportní kanál sám zabezpečený, protože server nemá žádný způsob, jak zjistit, jestli se z klienta navázal zabezpečený kanál. nebo MITM. Řešením v tomto scénáři je vytvořit propojení s vnějším kanálem TLS s kanálem interního ověřování, aby server mohl zjistit, jestli existuje MITM.  
  
> [!NOTE]
> Tato ukázka funguje jenom v případě, že je hostovaná ve službě IIS a nemůže pracovat na Cassini – Visual Studio Development Server, protože Cassini nepodporuje protokol HTTPS.  
  
> [!NOTE]
> Tato funkce je v tuto chvíli dostupná jenom ve Windows 7. Následující kroky jsou specifické pro systém Windows 7.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Nainstalujte Internetová informační služba z **ovládacích panelů**, **Přidat nebo odebrat programy**, **funkce systému Windows**.  
  
2. Nainstalujte **ověřování systému Windows** ve **funkcích systému Windows**, **Internetová informační služba**, **webové služby**, **zabezpečení**a **ověřování systému Windows**.  
  
3. Instalace **Windows Communication Foundation aktivace protokolem HTTP** v **součástech Windows**, **Microsoft .NET Framework 3.5.1**a **Windows Communication Foundation aktivace protokolem HTTP**.  
  
4. Tato ukázka vyžaduje, aby klient navázal zabezpečený kanál se serverem, takže vyžaduje přítomnost certifikátu serveru, který se dá nainstalovat z správce Internetová informační služba (IIS).  
  
    1. Otevřete Správce služby IIS. Otevřete **certifikáty serveru**, které se zobrazí na kartě **zobrazení funkcí** , pokud je vybrán kořenový uzel (název počítače).  
  
    2. Pro účely testování této ukázky vytvořte certifikát podepsaný svým držitelem. Pokud nechcete, aby Internet Explorer zobrazil výzvu k zadání nezabezpečeného certifikátu, nainstalujte certifikát do úložiště Důvěryhodné kořenové certifikační autority certifikátu.  
  
5. Otevřete podokno **Akce** pro výchozí web. Klikněte na **Upravit web**, **vazby**. Přidejte HTTPS jako typ, pokud ještě není přítomný, s číslem portu 443. Přiřaďte certifikát SSL, který jste vytvořili v předchozím kroku.  
  
6. Sestavte službu. Tím se vytvoří virtuální adresář ve službě IIS a zkopírují se soubory. dll,. svc a. config, jak je to nutné pro hostování služby na webu.  
  
7. Otevřete Správce služby IIS. Klikněte pravým tlačítkem na virtuální adresář (**ExtendedProtection**), který jste vytvořili v předchozím kroku. Vyberte **převést na aplikaci**.  
  
8. Otevřete modul **ověřování** ve Správci služby IIS pro tento virtuální adresář a povolte **ověřování systému Windows**.  
  
9. Otevřete **Rozšířené nastavení** v části **ověřování systému Windows** pro tento virtuální adresář a nastavte jej na hodnotu **požadováno**.  
  
10. Službu můžete otestovat přístupem k adrese URL HTTPS z okna prohlížeče (zadejte plně kvalifikovaný název domény). Pokud chcete získat přístup k této adrese URL ze vzdáleného počítače, ujistěte se, že je brána firewall otevřená pro všechna příchozí připojení HTTP a HTTPS.  
  
11. Otevřete konfigurační soubor klienta a zadejte plně kvalifikovaný název domény pro atribut klienta nebo adresy koncového bodu, který nahrazuje `<<full_machine_name>>`.  
  
12. Spusťte klienta. Klient komunikuje se službou, která vytvoří zabezpečený kanál a používá rozšířenou ochranu.  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Security\ExtendedProtection`
