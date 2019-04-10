---
title: Spouštění ukázek Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: db8a83da-95c1-4a21-a9d2-48caeb6398ea
ms.openlocfilehash: 32925caccee08c27e023d7ffae992e38cb496868
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59209213"
---
# <a name="running-the-windows-communication-foundation-samples"></a>Spouštění ukázek Windows Communication Foundation
Ukázky Windows Communication Foundation (WCF) můžete spustit v konfiguraci jednoho počítače nebo mezi počítači. Jako zadán, ukázky jsou připravené ke spuštění na jednom počítači. V konfiguraci mezi počítači je nutné upravit nastavení tohoto příkladu konfiguračního souboru. Následující postupy popisují, jak ve stejném počítači a mezi počítači konfiguracích spuštění ukázky. Všimněte si, že jsou změny v postupu pro služby hostované v Internetové informační služby (IIS) a ukázky v místním prostředí. Většina ukázek, které jsou hostované ve službě IIS; Podívejte se ukázkovými informacemi o souboru readme k určení, jak je hostovaná.  
  
 Na [!INCLUDE[wv](../../../../includes/wv-md.md)], ukázky, které se nehostují ve službě IIS vyžadují zvýšená oprávnění k registraci naslouchací proces se souborem Http.sys. Použít Httpcfg.exe zaregistrovat naslouchání adresy služby u účtu, který je služba spuštěná pod nebo spusťte službu z příkazového řádku s oprávněními správce.  
  
> [!NOTE]
>  Před vytvářejí nebo s některým z ukázky WCF, ujistěte se, jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-machine"></a>Ke spuštění ukázky ve stejném počítači  
  
1.  Pokud je služba hostována službou IIS, ujistěte se, že jste přístup ke službě pomocí prohlížeče zadáním následující adresy: `http://localhost/servicemodelsamples/service.svc`. Stránka s potvrzením má být zobrazena v odpovědi. Pokud se nezobrazí na stránce potvrzení, přečtěte si téma [tipy poradce při potížích pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
2.  Pokud služba je samoobslužně hostovaná, spusťte Service.exe z \service\bin ze složky specifické pro jazyk. Aktivita služby se zobrazí v okně konzoly služby.  
  
3.  Spustit Client.exe z \client\bin\\, ze složky specifické pro jazyk. Činnost klienta se zobrazí v okně konzoly klienta.  
  
4.  Pokud nejsou schopné komunikovat klienta a služby, přečtěte si téma [tipy poradce při potížích pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-machines"></a>Ke spuštění ukázky v počítačích  
  
1.  Pokud služba je hostována ve službě IIS:  
  
    1.  Na počítači služby vytvořte virtuální adresář s názvem ServiceModelSamples. Dávkový soubor, který je součástí Setupvroot.bat [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) je možné vytvořit na disku a virtuální adresář.  
  
    2.  Zkopírujte soubory programu služby z %SystemDrive%\Inetpub\wwwroot\servicemodelsamples do ServiceModelSamples virtuálního adresáře na počítači služby. Ujistěte se, že složku zahrnujete soubory v adresáři \bin.  
  
    3.  Testovací službě můžete dostat z klientského počítače pomocí prohlížeče.  
  
     Pokud je služba v místním prostředí:  
  
    1.  Na počítači, služby vytvořte adresář pro uložení souborů služby.  
  
    2.  Zkopírujte soubory programu služby ze složky \service\bin\ v rámci složky specifické pro jazyk do počítače služba.  
  
    3.  V konfiguračním souboru služby změňte hodnotu adresy definice koncového bodu tak, aby odpovídala nové adresu služby. Nahraďte všechny odkazy na "localhost" plně kvalifikovaný název domény v adrese.  
  
    4.  Service.exe spusťte z příkazového řádku.  
  
2.  Zkopírujte soubory programu klienta ze složky \client\bin\ v rámci složky specifické pro jazyk do klientského počítače.  
  
3.  Nastavte adresu koncového bodu.  
  
    1.  Pokud služba není spuštěna pod účtem domény, otevřete soubor konfigurace klienta a změňte hodnotu adresy definice koncového bodu tak, aby odpovídala nové adresu služby. Nahraďte všechny odkazy na "localhost" plně kvalifikovaný název domény v adrese.  
  
    2.  Pokud je služba spuštěna pod účtem domény, znovu vygenerovat konfiguraci klienta spuštěním Svcutil.exe na službu. Další informace o spouštění Svcutil.exe najdete v tématu [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md). Vygenerovaný soubor nahrazujícím konfiguračního souboru ve vzorku. Vygenerovaný konfigurační soubor obsahuje informace o dalších identity a obsahuje všechna nastavení požadovaná pro připojení ke koncovému bodu služby, i když jde o výchozí nastavení. Další informace o informace o identitě, naleznete v tématu [identita a ověřování služby](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md), a [ \<identity >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md).  
  
4.  Na klientském počítači a spusťte Client.exe z příkazového řádku.  
  
### <a name="to-debug-a-service"></a>Ladění služby  
  
1.  Sestavení řešení (klient a služba) používá **sestavení** nabídky nebo CTRL + SHIFT + B.  
  
2.  Pokud služba je hostována ve službě IIS:  
  
    1.  Aktivace služby pomocí prohlížeče tak, že zadáte adresu `http://localhost/servicemodelsamples/service.svc`.  
  
    2.  V řešení, zvolte **ladění** nabídky a **připojit k procesu** položky nabídky.  
  
    3.  Vyberte **Zobrazit procesy všech uživatelů** zaškrtávací políčko.  
  
    4.  Vyberte hostitele pracovní proces W3wp.exe ladění (vyberte ASPNet_wp.exe na Windows XP).  
  
3.  Teď můžete nastavit zarážky v kódu služby a povolit zarážky na výjimky.  
  
4.  Klikněte pravým tlačítkem na položku projektu klienta a zvolte **ladění**, **zahájit novou instanci**.  
  
### <a name="to-clean-up-after-the-sample"></a>K vyčištění po vzorku  
  
-   Pokud služba je hostována ve službě IIS pro účely zabezpečení, odeberte definici virtuální adresář a oprávnění udělené v kroků instalace, až budete hotovi s ukázkami.  
  
## <a name="see-also"></a>Viz také:

- [Ukázky vytváření Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md)
- [Řešení potíží s tipy pro ukázky WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))
