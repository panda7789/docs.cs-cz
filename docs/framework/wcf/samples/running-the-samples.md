---
title: Spouštění ukázek Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: db8a83da-95c1-4a21-a9d2-48caeb6398ea
ms.openlocfilehash: f4c7a7fa759d7339dee3d189540fb85f3883f828
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594566"
---
# <a name="running-the-windows-communication-foundation-samples"></a>Spouštění ukázek Windows Communication Foundation
Ukázky Windows Communication Foundation (WCF) je možné spustit v konfiguraci s jedním počítačem nebo mezi počítači. Jak je uvedeno, ukázky jsou připravené k provozu na jednom počítači. V konfiguraci mezi počítači je potřeba upravit nastavení konfiguračního souboru ukázky. Následující postupy vysvětlují, jak spustit ukázku ve stejném počítači a konfiguracích pro více počítačů. Všimněte si, že existují změny v krocích pro služby hostované v Internetová informační služba (IIS) a ve vzorcích pro místní hostování. Většina ukázek je hostována ve službě IIS; informace o tom, jak je hostovaný, najdete v ukázkovém souboru Readme.  
  
 V systému Windows Vista se v ukázkách, které nejsou hostované ve službě IIS, vyžaduje zvýšená oprávnění k registraci naslouchacího procesu pomocí HTTP. sys. Použijte Httpcfg. exe k registraci adres naslouchání služby u účtu, pod kterým je služba spuštěná, nebo spusťte službu z příkazového řádku spuštěného s oprávněními správce.  
  
> [!NOTE]
> Před vytvořením nebo spuštěním kterékoli z ukázek služby WCF se ujistěte, že jste provedli [jednorázovou proceduru nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-machine"></a>Spuštění ukázky na stejném počítači  
  
1. Pokud je služba hostovaná službou IIS, ujistěte se, že ke službě můžete přistupovat pomocí prohlížeče zadáním následující adresy: `http://localhost/servicemodelsamples/service.svc` . V odpovědi by se měla zobrazit Stránka s potvrzením. Pokud se nezobrazí stránka s potvrzením, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
2. Pokud je služba v místním prostředí, spusťte Service. exe z \service\bin ze složky specifické pro daný jazyk. Aktivita služby se zobrazí v okně konzoly služby.  
  
3. Spusťte soubor Client. exe z \client\bin \\ ze složky specifické pro jazyk. Aktivita klienta se zobrazí v okně konzoly klienta.  
  
4. Pokud klient a služba nejsou schopné komunikovat, přečtěte si [tipy pro řešení potíží s ukázkami služby WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-machines"></a>Spuštění ukázky napříč počítači  
  
1. Pokud je služba hostovaná ve službě IIS:  
  
    1. Na počítači služby vytvořte virtuální adresář s názvem ServiceModelSamples. Dávkový soubor Setupvroot. bat, který [je součástí procesu jednorázového nastavení pro Windows Communication Foundation ukázky,](one-time-setup-procedure-for-the-wcf-samples.md) lze použít k vytvoření adresáře disku a virtuálního adresáře.  
  
    2. Zkopírujte programové soubory služby z%SystemDrive%\Inetpub\wwwroot\servicemodelsamples do virtuálního adresáře ServiceModelSamples na počítači služby. Ujistěte se, že jste do adresáře \Bin zahrnuli soubory.  
  
    3. Otestujte, zda ke službě můžete přistupovat z klientského počítače pomocí prohlížeče.  
  
     Pokud je služba v místním prostředí:  
  
    1. Na počítači služby vytvořte adresář, ve kterém se budou uchovávat soubory služby.  
  
    2. Zkopírujte programové soubory služby ze složky \service\bin\ ve složce specifické pro daný jazyk do počítače služby.  
  
    3. V konfiguračním souboru služby změňte hodnotu adresy definice koncového bodu tak, aby odpovídala nové adrese vaší služby. Nahraďte všechny odkazy na "localhost" plně kvalifikovaným názvem domény v adrese.  
  
    4. Z příkazového řádku spusťte Service. exe.  
  
2. Zkopírujte soubory klientského programu ze složky \client\bin\ ve složce specifické pro daný jazyk do klientského počítače.  
  
3. Nastavte adresu koncového bodu.  
  
    1. Pokud služba není spuštěná pod účtem domény, otevřete soubor konfigurace klienta a změňte hodnotu adresy definice koncového bodu tak, aby odpovídala nové adrese vaší služby. Nahraďte všechny odkazy na "localhost" plně kvalifikovaným názvem domény v adrese.  
  
    2. Pokud je služba spuštěna pod účtem domény, znovu vygenerujte konfiguraci klienta spuštěním Svcutil. exe proti této službě. Další informace o spuštění Svcutil. exe najdete v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md). Místo konfiguračního souboru v ukázce použijte vygenerovaný soubor. Vygenerovaný konfigurační soubor obsahuje další informace o identitě a obsahuje všechna nastavení potřebná pro připojení ke koncovému bodu služby, i když se jedná o výchozí nastavení. Další informace o identitě najdete v tématu [Identita a ověřování služby](../feature-details/service-identity-and-authentication.md)a [\<identity>](../../configure-apps/file-schema/wcf/identity.md) .  
  
4. Na klientském počítači spusťte soubor Client. exe z příkazového řádku.  
  
### <a name="to-debug-a-service"></a>Ladění služby  
  
1. Sestavte řešení (klienta i služby) pomocí nabídky **sestavení** nebo CTRL + SHIFT + B.  
  
2. Pokud je služba hostovaná ve službě IIS:  
  
    1. Aktivujte službu pomocí prohlížeče zadáním adresy `http://localhost/servicemodelsamples/service.svc` .  
  
    2. V řešení vyberte nabídku **ladění** a položku nabídky **připojit k procesu** .  
  
    3. Zaškrtněte políčko **Zobrazit procesy všech uživatelů** .  
  
    4. Vyberte hostitelský pracovní proces W3wp. exe, který se má ladit (vyberte ASPNet_wp. exe v systému Windows XP).  
  
3. Nyní můžete nastavit zarážky v kódu služby a povolit zarážky na výjimky.  
  
4. Klikněte pravým tlačítkem myši na položku klientského projektu a vyberte možnost **ladit**, **spustit novou instanci**.  
  
### <a name="to-clean-up-after-the-sample"></a>Vyčištění po ukázce  
  
- Pokud je služba hostovaná ve službě IIS z důvodu zabezpečení, odeberte definici virtuálního adresáře a oprávnění udělená v krocích instalace po dokončení práce s ukázkami.  
  
## <a name="see-also"></a>Viz také

- [Ukázky vytváření Windows Communication Foundation](building-the-samples.md)
- [Tipy pro řešení potíží s ukázkami WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))
