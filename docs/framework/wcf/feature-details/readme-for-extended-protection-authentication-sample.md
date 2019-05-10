---
title: Soubor ReadMe pro ukázku rozšířené ochrany ověřování
ms.date: 03/30/2017
ms.assetid: 80bf2e97-398d-4db5-9040-d96478a2ccab
ms.openlocfilehash: 38f1c7e27162f79b436135be7fa9a499259ada9b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64643512"
---
# <a name="readme-for-extended-protection-authentication-sample"></a>Soubor ReadMe pro ukázku rozšířené ochrany ověřování
Rozšířená ochrana je iniciativy zabezpečení pro ochranu před útoky (typu MITM) man-in-the-middle, při které útočník ("man-in-the-middle") zachycuje přihlašovací údaje klienta a používá pro přístup k zabezpečeným prostředkům na serveru určené pro klienta.  
  
 Další informace najdete v tématu [rozšířené ochrany pro ověřování – přehled](../../../../docs/framework/wcf/feature-details/extended-protection-for-authentication-overview.md).  
  
> [!NOTE]
>  Tato ukázka funguje pouze v případě hostovaných ve službě IIS. Nepracuje na vývojový Server sady Visual Studio vzhledem k tomu, který nepodporuje protokol HTTPS.  
  
## <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1. Instalace služby IIS na počítači z panelu Přidat nebo odebrat programy -> funkce Windows.  
  
2. Zapněte ověřování Windows a funkce Windows: Internetová informační služba -> webové služby -> zabezpečení -> ověřování Windows.  
  
3. Aktivace protokolem HTTP zapněte v části funkce Windows: Rozhraní Microsoft .NET Framework 3.5.1 -> HTTP aktivace Windows Communication Foundation.  
  
4. Tato ukázka vyžaduje klienta k navázání zabezpečeného kanálu se serverem a proto vyžaduje přítomnost certifikát serveru, který si můžete nainstalovat pomocí Správce Internetové informační služby (IIS).  
  
    1. Otevřete Správce služby IIS -> certifikáty serveru (na kartě zobrazení funkce).  
  
    2. Pro účely testování tuto ukázku, můžete vytvořit certifikát podepsaný svým držitelem. (Pokud nechcete, aby se vás zeptá na certifikát, nebude zabezpečený v aplikaci Internet Explorer, můžete nainstalovat jej do úložiště Důvěryhodné kořenové certifikační autority).  
  
5. Přejděte do podokna akcí pro výchozí web. Klikněte na Upravit lokality -> vazby. Přidáte HTTPS jako typ, pokud ještě není k dispozici s číslem portu 443 a přiřadit certifikát SSL vytvořený v předchozím kroku.  
  
6. Vytvořte službu. To vytvoří virtuální adresář ve službě IIS za vás (ze zadaného ve vlastnostech projektu akci po sestavení) a zkopíruje soubory dll, svc a konfiguračním podle potřeby služby bude hostovaná na webu.  
  
7. Otevřete Správce služby IIS. Klikněte pravým tlačítkem na virtuální adresář (Rozšířená ochrana ExtendedProtection), který jste vytvořili v předchozím kroku a vyberte převést na aplikaci.  
  
8. Otevřete modul ověřování ve Správci služby IIS pro tento virtuální adresář a povolení ověřování Windows.  
  
9. Otevřít rozšířené nastavení pro Windows ověřování pro tento virtuální adresář a nastavte ho na povinné, protože v ukázce je odpovídající ExtendedProtection nastavená na hodnotu Always.  
  
10. Službu můžete otestovat přístup k adresu URL z okna prohlížeče. Pokud chcete přístup k této adrese URL z mezi počítači, ujistěte se, že brána firewall otevřená pro všechna příchozí připojení HTTP a HTTPS.  
  
11. Otevřete soubor konfigurace klienta a zadejte název počítače úplné \<klienta >- \<endpoint > – atribut adresy nahrazení << full_machine_name >>.  
  
12. Spustíte klienta. Klient komunikuje se služba navázáním zabezpečeného kanálu a použitím rozšířené ochrany na pozadí.
