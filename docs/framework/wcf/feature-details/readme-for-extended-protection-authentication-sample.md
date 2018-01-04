---
title: "Soubor ReadMe pro ukázku rozšířené ochrany ověřování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 80bf2e97-398d-4db5-9040-d96478a2ccab
caps.latest.revision: "3"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 78e787c129c0161e8730472124ee4162e2d1ba9d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="readme-for-extended-protection-authentication-sample"></a>Soubor ReadMe pro ukázku rozšířené ochrany ověřování
Rozšířená ochrana je initiative zabezpečení k ochraně proti útokům man-in-the-middle (typu MITM), ve kterých útočník ("man-in-the-middle") zachycuje pověření klienta a používá je pro přístup k zabezpečeným prostředkům na určený server klienta.  
  
 Další informace najdete v tématu [Rozšířená ochrana pro ověřování – přehled](../../../../docs/framework/wcf/feature-details/extended-protection-for-authentication-overview.md).  
  
> [!NOTE]
>  Tato ukázka funguje pouze při hostované ve službě IIS. Nefunguje na vývojový Server sady Visual Studio vzhledem k tomu, který nepodporuje protokol HTTPS.  
  
## <a name="to-set-up-build-and-run-the-sample"></a>Chcete nastavit, sestavit a spustit ukázku  
  
1.  Instalace služby IIS na počítači z panelu Přidat nebo odebrat programy -> funkce systému Windows.  
  
2.  Zapnout ověřování systému Windows v funkce systému Windows: Internetová informační služba -> Webová služba -> zabezpečení -> ověřování systému Windows.  
  
3.  Zapnout aktivace protokolu HTTP v funkce systému Windows: Microsoft .NET Framework 3.5.1 -> Aktivace Windows Communication Foundation HTTP.  
  
4.  Tato ukázka vyžaduje klienta k navázání zabezpečeného kanálu se serverem a proto vyžaduje přítomnost certifikát serveru, které můžete nainstalovat ze Správce Internetové informační služby (IIS).  
  
    1.  Otevřete Správce služby IIS -> certifikáty serveru (na kartě zobrazení funkce).  
  
    2.  Pro účely testování tuto ukázku, můžete vytvořit certifikát podepsaný svým držitelem. (Pokud nechcete, aby vás zeptá, certifikát nebude zabezpečené v aplikaci Internet Explorer, nebudete ho nainstalovat do úložiště Důvěryhodné kořenové certifikační autority).  
  
5.  Přejděte do podokna akce pro výchozí web. Klikněte na tlačítko Upravit lokality -> vazby. Přidejte HTTPS jako typ, pokud ještě není představovat číslo portu 443 a přiřadit certifikát SSL vytvořili v předchozím kroku.  
  
6.  Vytvořte službu. Tento virtuální adresář ve službě IIS pro vás vytvoří (z akce sestavení post zadána ve vlastnostech projektu) a zkopíruje soubory knihoven dll, .svc a konfigurace podle potřeby pro službu být hostovaná na webu.  
  
7.  Otevřete Správce služby IIS. Klikněte pravým tlačítkem na virtuální adresář (ExtendedProtection), který jste vytvořili v předchozím kroku a vyberte převod na aplikace.  
  
8.  Otevřete modul ověřování ve Správci služby IIS pro tento virtuální adresář a povolit ověřování systému Windows.  
  
9. Otevřete rozšířená nastavení pro ověřování systému Windows pro tento virtuální adresář a nastavte ji na povinné, protože v ukázce odpovídající nastavení ExtendedProtection nastavena vždy.  
  
10. Službu můžete otestovat přístup k adresu URL z okna prohlížeče. Pokud chcete přístup k této adrese URL z křížové počítače, ujistěte se, že brána firewall, je otevřené pro všechna příchozí připojení HTTP a HTTPS.  
  
11. Otevřete soubor konfigurace klienta a zadejte název počítače úplné \<klienta >- \<koncový bod >-atribut adresu, nahraďte << full_machine_name >>.  
  
12. Spuštění klienta. Klient komunikuje se služba navázáním zabezpečeného kanálu a použitím rozšířené ochrany v pozadí.
