---
title: "Zásady rozšířené ochrany"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e2616a10-317e-4c34-8023-0c015a80a82f
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1e2d9389487bb95fe13b5c12b6f861ae30e29677
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="extended-protection-policy"></a>Zásady rozšířené ochrany
Rozšířená ochrana je initiative zabezpečení pro ochranu proti útokům man-in-the-middle (typu MITM). Útoky typu MITM je ohrožení zabezpečení, ve kterém MITM přijímá pověření klienta a předává je na server.  
  
## <a name="demonstrates"></a>Demonstruje  
 Rozšířená ochrana  
  
## <a name="discussion"></a>Diskusní  
 Pokud aplikace ověřit pomocí protokolu Kerberos, algoritmus Digest ani protokol NTLM pomocí protokolu HTTPS, je nejprve vytvořit kanál úroveň zabezpečení TLS (Transport) a pak ověřování probíhá pomocí zabezpečený kanál. Však neexistuje žádná vazba mezi klíč relace generované SSL a klíč relace vygenerovaných během ověřování. Všechny MITM můžete určit sám sebe mezi klientem a serverem a spustit předávání žádosti z klienta, i v případě, že kanál přenosu samotného je bezpečné, protože server nemá žádný způsob, jak zjistit, zda zabezpečený kanál je vytvořený z klienta nebo MITM. Řešení v tomto scénáři je vytvoření vazby s kanálem vnitřní ověřování vnější kanál TLS tak, že server může zjistit, jestli je MITM.  
  
> [!NOTE]
>  Tato ukázka pouze funguje, když hostované ve službě IIS a nemůže pracovat na Cassini – vývojový Server sady Visual Studio, protože Cassini nepodporuje protokol HTTPS.  
  
> [!NOTE]
>  Tato funkce je aktuálně k dispozici pouze v systému Windows 7. Následující kroky jsou specifické pro systém Windows 7.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Nainstalujte Internetovou informační službu z **ovládací panely**, **přidat nebo odebrat programy**, **funkce systému Windows**.  
  
2.  Nainstalujte **ověřování systému Windows** v **funkce systému Windows**, **Internetová informační služba**, **webové služby**,  **Zabezpečení**, a **ověřování systému Windows**.  
  
3.  Nainstalujte **aktivace Windows Communication Foundation HTTP** v **funkce systému Windows**, **rozhraní Microsoft .NET Framework 3.5.1**, a **komunikaci Windows Aktivace Foundation HTTP**.  
  
4.  Tato ukázka vyžaduje, aby klient k navázání zabezpečeného kanálu se serverem, takže vyžaduje přítomnost certifikát serveru, které můžete nainstalovat ze Správce Internetové informační služby (IIS).  
  
    1.  Otevřete Správce služby IIS. Otevřete **certifikáty serveru**, který se objevuje v **zobrazení funkce** kartě, pokud je vybrána kořenového uzlu (název počítače).  
  
    2.  Pro účely testování této ukázce, vytvořte certifikát podepsaný svým držitelem. Pokud nechcete, aby se vás zeptá, certifikát nebude zabezpečené v aplikaci Internet Explorer, nainstalujte certifikát do úložiště Důvěryhodné kořenové certifikační autority.  
  
5.  Otevřete **akce** podokno pro výchozí web. Klikněte na tlačítko **web upravit**, **vazby**. Přidat HTTPS jako typ Pokud již nejsou přítomny, s číslem portu 443. Přiřadíte certifikát SSL vytvořili v předchozím kroku.  
  
6.  Vytvořte službu. To vytvoří virtuální adresář ve službě IIS a zkopíruje soubory .dll, .svc a .config podle potřeby má být hostovaná na webu pro službu.  
  
7.  Otevřete Správce služby IIS. Klikněte pravým tlačítkem na virtuální adresář (**ExtendedProtection**), který byl vytvořen v předchozím kroku. Vyberte **převést na aplikaci**.  
  
8.  Otevřete **ověřování** modulu ve Správci služby IIS pro tento virtuální adresář a povolit **ověřování systému Windows**.  
  
9. Otevřete **Upřesnit nastavení** pod **ověřování systému Windows** pro tento virtuální adresář a nastavte ji na **požadované**.  
  
10. Službu můžete otestovat přístup k adresu URL HTTPS z okna prohlížeče (zadejte název a plně kvalifikované domény). Pokud chcete přístup k této adrese URL ze vzdáleného počítače, ujistěte se, že brána firewall, je otevřené pro všechna příchozí připojení HTTP a HTTPS.  
  
11. Otevřete konfigurační soubor klienta a zadejte název plně kvalifikované domény pro atribut adresa klienta nebo koncový bod, který nahrazuje `<<full_machine_name>>`.  
  
12. Spuštění klienta. Klient komunikuje se službou, která vytváří zabezpečený kanál a používá rozšířené ochrany.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Security\ExtendedProtection`
