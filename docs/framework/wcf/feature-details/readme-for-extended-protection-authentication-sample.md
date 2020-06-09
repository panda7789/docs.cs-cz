---
title: Soubor ReadMe pro ukázku rozšířené ochrany ověřování
ms.date: 03/30/2017
ms.assetid: 80bf2e97-398d-4db5-9040-d96478a2ccab
ms.openlocfilehash: 9b0a3535282a1fcc1103651f5601459e80d3d8d4
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601098"
---
# <a name="readme-for-extended-protection-authentication-sample"></a>Soubor ReadMe pro ukázku rozšířené ochrany ověřování

Rozšířená ochrana je bezpečnostní iniciativa pro ochranu proti útokům MITM (man-in-the-middle), kdy útočník ("muž-in-the-middle") zachycuje přihlašovací údaje klienta a používá je k přístupu k zabezpečeným prostředkům na zamýšleném serveru klienta.

Další informace najdete v tématu [Rozšířená ochrana pro ověřování – přehled](extended-protection-for-authentication-overview.md).

> [!NOTE]
> Tato ukázka funguje jenom v případě, že je hostovaná ve službě IIS. Nefunguje na vývojovém serveru sady Visual Studio, protože nepodporuje protokol HTTPS.

## <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky

1. Nainstalujte službu IIS na počítači pomocí ovládacího panelu Přidat nebo odebrat programy – > funkce Windows.

2. Zapnout ověřování systému Windows ve funkcích Windows: Internetová informační služba-> World World World World Services-> zabezpečení – > ověřování systému Windows.

3. Zapnutí aktivace protokolem HTTP v součástech systému Windows: Microsoft .NET Framework 3.5.1 – > Windows Communication Foundation aktivace protokolem HTTP.

4. Tato ukázka vyžaduje, aby klient navázal zabezpečený kanál se serverem, takže vyžaduje přítomnost certifikátu serveru, který se dá nainstalovat z správce Internetová informační služba (IIS).

    1. Otevřete Správce služby IIS-> certifikáty serveru (na kartě zobrazení funkcí).

    2. Pro účely testování této ukázky můžete vytvořit certifikát podepsaný svým držitelem. (Pokud nechcete, aby Internet Explorer zobrazil výzvu k tomu, že certifikát není zabezpečený, můžete ho nainstalovat v úložišti Důvěryhodné kořenové certifikační autority certifikátu).

5. Přejít do podokna akce pro výchozí web. Klikněte na Upravit vazby > webů. Přidejte HTTPS jako typ, pokud ještě neexistuje, s číslem portu 443 a přiřaďte certifikát SSL, který jste vytvořili v předchozím kroku.

6. Sestavte službu. Tím se vytvoří virtuální adresář ve službě IIS pro vás (od akce po sestavení určené ve vlastnostech projektu) a zkopírování souborů DLL, svc a config, jak je to nutné, aby byla služba hostitelem webu.

7. Otevřete Správce služby IIS. Klikněte pravým tlačítkem na virtuální adresář (ExtendedProtection), který jste vytvořili v předchozím kroku, a vyberte převést na aplikaci.

8. Otevřete modul ověřování ve Správci služby IIS pro tento virtuální adresář a povolte ověřování systému Windows.

9. Otevřete upřesňující nastavení pro ověřování systému Windows pro tento virtuální adresář a nastavte jej na požadováno, protože v ukázce je odpovídající nastavení ExtendedProtection nastaveno na vždy.

10. Službu můžete otestovat přístupem k adrese URL z okna prohlížeče. Pokud chcete získat přístup k této adrese URL z více počítačů, ujistěte se, že je brána firewall otevřená pro všechna příchozí připojení HTTP a HTTPS.

11. Otevřete konfigurační soubor klienta a zadejte úplný název počítače pro \<client>  -  \<endpoint> atribut-address a nahraďte ho \<full_machine_name> .

12. Spusťte klienta. Klient komunikuje se službou vytvořením zabezpečeného kanálu a použitím rozšířené ochrany v rámci pokrývání.
