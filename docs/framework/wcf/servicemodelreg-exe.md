---
title: Nástroj ServiceModel Registration (ServiceModelReg.exe)
ms.date: 03/30/2017
ms.assetid: 396ec5ae-e34f-4c64-a164-fcf50e86b6ac
ms.openlocfilehash: a6f65ccc6caa0a7e496e7de8c83259ab48903753
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183110"
---
# <a name="servicemodel-registration-tool-servicemodelregexe"></a><span data-ttu-id="c21fd-102">Nástroj ServiceModel Registration (ServiceModelReg.exe)</span><span class="sxs-lookup"><span data-stu-id="c21fd-102">ServiceModel Registration Tool (ServiceModelReg.exe)</span></span>
<span data-ttu-id="c21fd-103">Tento nástroj příkazového řádku poskytuje možnost spravovat registraci komponent WCF a WF na jednom počítači.</span><span class="sxs-lookup"><span data-stu-id="c21fd-103">This command-line tool provides the ability to manage the registration of WCF and WF components on a single machine.</span></span> <span data-ttu-id="c21fd-104">Za normálních okolností byste neměli používat tento nástroj jako WCF a WF komponenty jsou konfigurovány při instalaci.</span><span class="sxs-lookup"><span data-stu-id="c21fd-104">Under normal circumstances you should not need to use this tool as WCF and WF components are configured when installed.</span></span> <span data-ttu-id="c21fd-105">Pokud však dochází k potížím s aktivací služby, můžete se pokusit zaregistrovat součásti pomocí tohoto nástroje.</span><span class="sxs-lookup"><span data-stu-id="c21fd-105">But if you are experiencing problems with service activation, you can try to register the components using this tool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c21fd-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c21fd-106">Syntax</span></span>  
  
```console  
ServiceModelReg.exe[(-ia|-ua|-r)|((-i|-u) -c:<command>)] [-v|-q] [-nologo] [-?]  
```  
  
## <a name="remarks"></a><span data-ttu-id="c21fd-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c21fd-107">Remarks</span></span>  
 <span data-ttu-id="c21fd-108">Nástroj lze nalézt v následujícím umístění:</span><span class="sxs-lookup"><span data-stu-id="c21fd-108">The tool can be found in the following location:</span></span>  
  
 <span data-ttu-id="c21fd-109">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="c21fd-109">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation</span></span>\  
  
> [!NOTE]
> <span data-ttu-id="c21fd-110">Při spuštění nástroje ServiceModel Registration Tool v systému Windows Vista nemusí dialogové okno **Funkce systému Windows** odrážet, že je zapnuta možnost **aktivace http verze systému Windows Communication Foundation** v rámci rozhraní Microsoft **.NET Framework 3.0.**</span><span class="sxs-lookup"><span data-stu-id="c21fd-110">When the ServiceModel Registration Tool is run on Windows Vista, the **Windows Features** dialog may not reflect that the **Windows Communication Foundation HTTP Activation** option under **Microsoft .NET Framework 3.0** is turned on.</span></span> <span data-ttu-id="c21fd-111">Dialogové okno **Funkce systému Windows** lze získat klepnutím na tlačítko **Start**, potom klepněte na tlačítko **Spustit** a potom zadáním **příkazu OptionalFeatures**.</span><span class="sxs-lookup"><span data-stu-id="c21fd-111">The **Windows Features** dialog can be accessed by clicking **Start**, then click **Run** and then typing **OptionalFeatures**.</span></span>  
  
 <span data-ttu-id="c21fd-112">Následující tabulky popisují možnosti, které lze použít s ServiceModelReg.exe.</span><span class="sxs-lookup"><span data-stu-id="c21fd-112">The following tables describe the options that can be used with ServiceModelReg.exe.</span></span>  
  
|<span data-ttu-id="c21fd-113">Možnost</span><span class="sxs-lookup"><span data-stu-id="c21fd-113">Option</span></span>|<span data-ttu-id="c21fd-114">Popis</span><span class="sxs-lookup"><span data-stu-id="c21fd-114">Description</span></span>|  
|------------|-----------------|  
|`-ia`|<span data-ttu-id="c21fd-115">Nainstaluje všechny součásti WCF a WF.</span><span class="sxs-lookup"><span data-stu-id="c21fd-115">Installs all WCF and WF components.</span></span>|  
|`-ua`|<span data-ttu-id="c21fd-116">Odinstaluje všechny součásti WCF a WF.</span><span class="sxs-lookup"><span data-stu-id="c21fd-116">Uninstalls all WCF and WF components.</span></span>|  
|`-r`|<span data-ttu-id="c21fd-117">Opravuje všechny součásti WCF a WF.</span><span class="sxs-lookup"><span data-stu-id="c21fd-117">Repairs all WCF and WF components.</span></span>|  
|`-i`|<span data-ttu-id="c21fd-118">Nainstaluje součásti WCF a WF zadané pomocí –c.</span><span class="sxs-lookup"><span data-stu-id="c21fd-118">Installs WCF and WF components specified with –c.</span></span>|  
|`-u`|<span data-ttu-id="c21fd-119">Odinstaluje součásti WCF a WF zadané pomocí –c.</span><span class="sxs-lookup"><span data-stu-id="c21fd-119">Uninstalls WCF and WF components specified with –c.</span></span>|  
|`-c`|<span data-ttu-id="c21fd-120">Nainstaluje nebo odinstaluje součást:</span><span class="sxs-lookup"><span data-stu-id="c21fd-120">Installs or uninstalls a component:</span></span><br /><br /> <span data-ttu-id="c21fd-121">- httpnamespace - HTTP Namespace rezervace</span><span class="sxs-lookup"><span data-stu-id="c21fd-121">-   httpnamespace – HTTP Namespace Reservation</span></span><br /><span data-ttu-id="c21fd-122">- tcpportsharing – služba sdílení portů TCP</span><span class="sxs-lookup"><span data-stu-id="c21fd-122">-   tcpportsharing – TCP port sharing service</span></span><br /><span data-ttu-id="c21fd-123">- tcpaktivace – služba aktivace TCP (nepodporovaná na profilu klienta .NET 4)</span><span class="sxs-lookup"><span data-stu-id="c21fd-123">-   tcpactivation – TCP activation service (unsupported on .NET 4 Client Profile)</span></span><br /><span data-ttu-id="c21fd-124">- namedpipeactivation – služba aktivace pojmenovaného kanálu (nepodporovaná na profilu klienta .NET 4</span><span class="sxs-lookup"><span data-stu-id="c21fd-124">-   namedpipeactivation – Named pipe activation service (unsupported on .NET 4 Client Profile</span></span><br /><span data-ttu-id="c21fd-125">- msmqaktivace – služba aktivace služby MSMQ (nepodporovaná na profilu klienta .NET 4</span><span class="sxs-lookup"><span data-stu-id="c21fd-125">-   msmqactivation – MSMQ activation service (unsupported on .NET 4 Client Profile</span></span><br /><span data-ttu-id="c21fd-126">- etw - ETW události trasování manifestů (Windows Vista nebo novější)</span><span class="sxs-lookup"><span data-stu-id="c21fd-126">-   etw – ETW event tracing manifests (Windows Vista or later)</span></span>|  
|`-q`|<span data-ttu-id="c21fd-127">Tichý režim (pouze zobrazení chyby při protokolování)</span><span class="sxs-lookup"><span data-stu-id="c21fd-127">Quiet mode (only display error logging)</span></span>|  
|`-v`|<span data-ttu-id="c21fd-128">Podrobný režim.</span><span class="sxs-lookup"><span data-stu-id="c21fd-128">Verbose mode.</span></span>|  
|`-nologo`|<span data-ttu-id="c21fd-129">Potlačí autorská práva a bannerové zprávy.</span><span class="sxs-lookup"><span data-stu-id="c21fd-129">Suppresses the copyright and banner message.</span></span>|  
|`-?`|<span data-ttu-id="c21fd-130">Zobrazí text nápovědy.</span><span class="sxs-lookup"><span data-stu-id="c21fd-130">Displays help text</span></span>|  
  
## <a name="fixing-the-fileloadexception-error"></a><span data-ttu-id="c21fd-131">Oprava chyby FileLoadException</span><span class="sxs-lookup"><span data-stu-id="c21fd-131">Fixing the FileLoadException Error</span></span>  
 <span data-ttu-id="c21fd-132">Pokud jste nainstalovali předchozí verze WCF v počítači, může dojít k `FileLoadFoundException` chybě při spuštění nástroje ServiceModelReg zaregistrovat novou instalaci.</span><span class="sxs-lookup"><span data-stu-id="c21fd-132">If you installed previous versions of WCF on your machine, you may get a `FileLoadFoundException` error when you run the ServiceModelReg tool to register a new installation.</span></span> <span data-ttu-id="c21fd-133">K tomu může dojít i v případě, že jste ručně odebrali soubory z předchozí instalace, ale ponechali nastavení machine.config beze změny.</span><span class="sxs-lookup"><span data-stu-id="c21fd-133">This can happen even if you have manually removed files from the previous install, but left the machine.config settings intact.</span></span>  
  
 <span data-ttu-id="c21fd-134">Chybová zpráva je podobná následující.</span><span class="sxs-lookup"><span data-stu-id="c21fd-134">The error message is similar to the following.</span></span>  
  
```console  
Error: System.IO.FileLoadException: Could not load file or assembly 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040)  
File name: 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'  
```  
  
 <span data-ttu-id="c21fd-135">Z chybové zprávy byste si měli uvědomit, že sestavení System.ServiceModel verze 2.0.0.0 bylo nainstalováno včasnou verzí Verze CTP (Customer Technology Preview).</span><span class="sxs-lookup"><span data-stu-id="c21fd-135">You should note from the error message that the System.ServiceModel Version 2.0.0.0 assembly was installed by an early Customer Technology Preview (CTP) release.</span></span> <span data-ttu-id="c21fd-136">Aktuální verze vydaného sestavení System.ServiceModel je 3.0.0.0.</span><span class="sxs-lookup"><span data-stu-id="c21fd-136">The current version of the System.ServiceModel assembly released is 3.0.0.0 instead.</span></span> <span data-ttu-id="c21fd-137">Proto k tomuto problému dochází, pokud chcete nainstalovat oficiální verzi WCF v počítači, kde byla nainstalována časná verze CTP WCF, ale není zcela odinstalována.</span><span class="sxs-lookup"><span data-stu-id="c21fd-137">Therefore, this issue is encountered when you want to install the official WCF release on a machine where an early CTP release of WCF was installed, but not completely uninstalled.</span></span>  
  
 <span data-ttu-id="c21fd-138">ServiceModelReg.exe nelze vyčistit předchozí verze položky, ani může zaregistrovat nové verze položky.</span><span class="sxs-lookup"><span data-stu-id="c21fd-138">ServiceModelReg.exe cannot clean up prior version entries, nor can it register the new version's entries.</span></span> <span data-ttu-id="c21fd-139">Jediným řešením je ruční úprava souboru machine.config. Tento soubor můžete najít v následujícím umístění.</span><span class="sxs-lookup"><span data-stu-id="c21fd-139">The only workaround is to manually edit machine.config. You can locate this file at the following location.</span></span>  
  
```console  
%windir%\Microsoft.NET\Framework\v2.0.50727\config\machine.config
```  
  
 <span data-ttu-id="c21fd-140">Pokud používáte WCF v 64bitovém počítači, měli byste také upravit stejný soubor v tomto umístění.</span><span class="sxs-lookup"><span data-stu-id="c21fd-140">If you are running WCF on a 64-bit machine, you should also edit the same file at this location.</span></span>  
  
```console  
%windir%\Microsoft.NET\Framework64\v2.0.50727\config\machine.config
```  
  
 <span data-ttu-id="c21fd-141">Vyhledejte všechny uzly XML v tomto souboru, které odkazují na "System.ServiceModel, Version=2.0.0.0", odstraňte je a všechny podřízené uzly.</span><span class="sxs-lookup"><span data-stu-id="c21fd-141">Locate any XML nodes in this file that refer to "System.ServiceModel, Version=2.0.0.0", delete them and any child nodes.</span></span> <span data-ttu-id="c21fd-142">Uložte soubor a znovu spusťte serviceModelReg.exe tento problém vyřeší.</span><span class="sxs-lookup"><span data-stu-id="c21fd-142">Save the file and re-run ServiceModelReg.exe resolves this problem.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="c21fd-143">Příklady</span><span class="sxs-lookup"><span data-stu-id="c21fd-143">Examples</span></span>  
 <span data-ttu-id="c21fd-144">Následující příklady ukazují, jak používat nejběžnější možnosti nástroje ServiceModelReg.exe.</span><span class="sxs-lookup"><span data-stu-id="c21fd-144">The following examples show how to use the most common options of the ServiceModelReg.exe tool.</span></span>  
  
```console  
ServiceModelReg.exe -ia  
  Installs all components  
ServiceModelReg.exe -i -c:httpnamespace -c:etw  
  Installs HTTP namespace reservation and ETW manifests  
ServiceModelReg.exe -u -c:etw  
  Uninstalls ETW manifests  
ServiceModelReg.exe -r  
  Repairs an extended install  
```
