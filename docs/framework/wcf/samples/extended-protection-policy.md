---
title: Zásady rozšířené ochrany
ms.date: 03/30/2017
ms.assetid: e2616a10-317e-4c34-8023-0c015a80a82f
ms.openlocfilehash: 645b48b3c7ce3daaaedac372ba5ba6fd5edfc8f8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61990168"
---
# <a name="extended-protection-policy"></a>Zásady rozšířené ochrany
Rozšířená ochrana je iniciativy zabezpečení pro ochranu před útoky man-in-the-middle (typu MITM). Útoky MITM je bezpečnostní hrozbu, ve kterém MITM přijímá pověření klienta a předá jej do serveru.  
  
## <a name="demonstrates"></a>Demonstruje  
 Rozšířená ochrana  
  
## <a name="discussion"></a>Diskuse  
 Když aplikace ověřování pomocí protokolu Kerberos, hodnotou hash nebo NTLM pomocí protokolu HTTPS, prvním vytváření kanálu úroveň TLS (Transport Security) a pak ověřování probíhá pomocí zabezpečeného kanálu. Neexistuje ale žádná vazba mezi klíč relace generovaných SSL a klíče relace vygenerovaných během ověřování. Žádné MITM můžete určit sám mezi klientem a serverem a spusťte předávání žádosti z klienta, i když samotný kanál přenosu je zabezpečená, protože server nemá žádnou možnost zjistit, zda zabezpečený kanál byl vytvořen z klienta nebo MITM. Řešení v tomto scénáři se k vytvoření vazby vnější kanál TLS s kanálem vnitřní ověřování tak, aby server dokáže detekovat, pokud je MITM.  
  
> [!NOTE]
>  Tato ukázka pouze funguje, když jsou hostované ve službě IIS a nemůže fungovat pro Cassini – vývojový Server sady Visual Studio, protože Cassini nepodporuje protokol HTTPS.  
  
> [!NOTE]
>  Tato funkce je aktuálně k dispozici pouze ve Windows 7. Následující kroky jsou specifická pro Windows 7.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1. Nainstalujte Internetovou informační službu z **ovládací panely**, **přidat nebo odebrat programy**, **funkce Windows**.  
  
2. Nainstalujte **ověřování Windows** v **funkce Windows**, **Internetová informační služba**, **webové služby**,  **Zabezpečení**, a **ověřování Windows**.  
  
3. Nainstalujte **aktivace Windows Communication Foundation HTTP** v **funkce Windows**, **rozhraní Microsoft .NET Framework 3.5.1**, a **komunikace Windows Aktivace protokolu HTTP Foundation**.  
  
4. Tato ukázka vyžaduje klientům navázat zabezpečené připojení k serveru, takže vyžaduje přítomnost certifikát serveru, který si můžete nainstalovat pomocí Správce Internetové informační služby (IIS).  
  
    1. Otevřete Správce služby IIS. Otevřít **certifikáty serveru**, který se objevuje v **zobrazení funkce** kartu, pokud je vybrána kořenový uzel (název počítače).  
  
    2. Pro účely testování této ukázce, vytvořte certifikát podepsaný svým držitelem. Pokud nechcete, aby se vás zeptá na certifikát, nebude zabezpečený v aplikaci Internet Explorer, nainstalujte certifikát do úložiště Důvěryhodné kořenové certifikační autority.  
  
5. Otevřít **akce** podokno pro výchozí web. Klikněte na tlačítko **upravit web**, **vazby**. Přidat jako typ protokolu HTTPS, pokud není již existuje s číslem portu 443. Přiřadíte certifikát SSL vytvořený v předchozím kroku.  
  
6. Vytvořte službu. Vytvoří virtuální adresář služby IIS a zkopíruje soubory .dll, .svc a .config podle potřeby pro službu bude hostovaná na webu.  
  
7. Otevřete Správce služby IIS. Klikněte pravým tlačítkem na virtuální adresář (**ExtendedProtection**), který byl vytvořen v předchozím kroku. Vyberte **převést na aplikaci**.  
  
8. Otevřít **ověřování** modul ve Správci služby IIS pro tento virtuální adresář a povolit **ověřování Windows**.  
  
9. Otevřít **Upřesnit nastavení** pod **ověřování Windows** pro tento virtuální adresář a nastavte ho na **vyžaduje**.  
  
10. Službu můžete otestovat přístup k adresu URL HTTPS z okna prohlížeče (zadejte plně kvalifikovaný název domény). Pokud chcete k této adrese URL přístup ze vzdáleného počítače, ujistěte se, že brána firewall otevřená pro všechna příchozí připojení HTTP a HTTPS.  
  
11. Otevřete soubor konfigurace klienta a zadejte název plně kvalifikované domény pro atribut adresa klienta nebo koncový bod, který nahrazuje `<<full_machine_name>>`.  
  
12. Spustíte klienta. Klient komunikuje se službou, která vytváří zabezpečený kanál a použije rozšířenou ochranu.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Security\ExtendedProtection`
