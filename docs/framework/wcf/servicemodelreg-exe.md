---
title: Nástroj ServiceModel Registration (ServiceModelReg.exe)
description: Pomocí tohoto nástroje příkazového řádku můžete spravovat registraci komponent WCF a WF na jednom počítači, pokud dojde k potížím s aktivací služby.
ms.date: 03/30/2017
ms.assetid: 396ec5ae-e34f-4c64-a164-fcf50e86b6ac
ms.openlocfilehash: 347b1b8071abe7d8eb7e16ffd879c1fdb9825bc7
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245892"
---
# <a name="servicemodel-registration-tool-servicemodelregexe"></a><span data-ttu-id="0dc89-103">Nástroj ServiceModel Registration (ServiceModelReg.exe)</span><span class="sxs-lookup"><span data-stu-id="0dc89-103">ServiceModel Registration Tool (ServiceModelReg.exe)</span></span>
<span data-ttu-id="0dc89-104">Tento nástroj příkazového řádku poskytuje možnost spravovat registraci komponent WCF a WF na jednom počítači.</span><span class="sxs-lookup"><span data-stu-id="0dc89-104">This command-line tool provides the ability to manage the registration of WCF and WF components on a single machine.</span></span> <span data-ttu-id="0dc89-105">Za normálních okolností byste neměli tento nástroj používat, protože komponenty technologie WCF a WF se nakonfigurují po instalaci.</span><span class="sxs-lookup"><span data-stu-id="0dc89-105">Under normal circumstances you should not need to use this tool as WCF and WF components are configured when installed.</span></span> <span data-ttu-id="0dc89-106">Pokud ale máte problémy s aktivací služby, můžete se pokusit zaregistrovat komponenty pomocí tohoto nástroje.</span><span class="sxs-lookup"><span data-stu-id="0dc89-106">But if you are experiencing problems with service activation, you can try to register the components using this tool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0dc89-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="0dc89-107">Syntax</span></span>  
  
```console  
ServiceModelReg.exe[(-ia|-ua|-r)|((-i|-u) -c:<command>)] [-v|-q] [-nologo] [-?]  
```  
  
## <a name="remarks"></a><span data-ttu-id="0dc89-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0dc89-108">Remarks</span></span>  
 <span data-ttu-id="0dc89-109">Nástroj najdete v následujícím umístění:</span><span class="sxs-lookup"><span data-stu-id="0dc89-109">The tool can be found in the following location:</span></span>  
  
 <span data-ttu-id="0dc89-110">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation </span><span class="sxs-lookup"><span data-stu-id="0dc89-110">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation</span></span>\  
  
> [!NOTE]
> <span data-ttu-id="0dc89-111">Když se nástroj pro registraci ServiceModel v systému Windows Vista spustí, dialog **funkcí Windows** se nemusí projevit, protože je zapnutá možnost **Windows Communication Foundation aktivace protokolem HTTP** pod **Microsoft .NET Framework 3,0** .</span><span class="sxs-lookup"><span data-stu-id="0dc89-111">When the ServiceModel Registration Tool is run on Windows Vista, the **Windows Features** dialog may not reflect that the **Windows Communication Foundation HTTP Activation** option under **Microsoft .NET Framework 3.0** is turned on.</span></span> <span data-ttu-id="0dc89-112">K dialogovému oknu **funkcí Windows** se dostanete tak, že kliknete na **Start**, pak na **Spustit** a pak zadáte **optionalfeatures**.</span><span class="sxs-lookup"><span data-stu-id="0dc89-112">The **Windows Features** dialog can be accessed by clicking **Start**, then click **Run** and then typing **OptionalFeatures**.</span></span>  
  
 <span data-ttu-id="0dc89-113">V následujících tabulkách jsou popsány možnosti, které lze použít s ServiceModelReg.exe.</span><span class="sxs-lookup"><span data-stu-id="0dc89-113">The following tables describe the options that can be used with ServiceModelReg.exe.</span></span>  
  
|<span data-ttu-id="0dc89-114">Možnost</span><span class="sxs-lookup"><span data-stu-id="0dc89-114">Option</span></span>|<span data-ttu-id="0dc89-115">Description</span><span class="sxs-lookup"><span data-stu-id="0dc89-115">Description</span></span>|  
|------------|-----------------|  
|`-ia`|<span data-ttu-id="0dc89-116">Nainstaluje všechny součásti WCF a WF.</span><span class="sxs-lookup"><span data-stu-id="0dc89-116">Installs all WCF and WF components.</span></span>|  
|`-ua`|<span data-ttu-id="0dc89-117">Odinstaluje všechny součásti WCF a WF.</span><span class="sxs-lookup"><span data-stu-id="0dc89-117">Uninstalls all WCF and WF components.</span></span>|  
|`-r`|<span data-ttu-id="0dc89-118">Opraví všechny součásti WCF a WF.</span><span class="sxs-lookup"><span data-stu-id="0dc89-118">Repairs all WCF and WF components.</span></span>|  
|`-i`|<span data-ttu-id="0dc89-119">Nainstaluje WCF a součásti WF zadané pomocí – c.</span><span class="sxs-lookup"><span data-stu-id="0dc89-119">Installs WCF and WF components specified with –c.</span></span>|  
|`-u`|<span data-ttu-id="0dc89-120">Odinstaluje komponenty WCF a WF zadané pomocí – c.</span><span class="sxs-lookup"><span data-stu-id="0dc89-120">Uninstalls WCF and WF components specified with –c.</span></span>|  
|`-c`|<span data-ttu-id="0dc89-121">Nainstaluje nebo odinstaluje součást:</span><span class="sxs-lookup"><span data-stu-id="0dc89-121">Installs or uninstalls a component:</span></span><br /><br /> <span data-ttu-id="0dc89-122">-httpnamespace – rezervace oboru názvů HTTP</span><span class="sxs-lookup"><span data-stu-id="0dc89-122">-   httpnamespace – HTTP Namespace Reservation</span></span><br /><span data-ttu-id="0dc89-123">-tcpportsharing – služba sdílení portů TCP</span><span class="sxs-lookup"><span data-stu-id="0dc89-123">-   tcpportsharing – TCP port sharing service</span></span><br /><span data-ttu-id="0dc89-124">-tcpactivation – aktivační služba TCP (nepodporovaná v profilu klienta .NET 4)</span><span class="sxs-lookup"><span data-stu-id="0dc89-124">-   tcpactivation – TCP activation service (unsupported on .NET 4 Client Profile)</span></span><br /><span data-ttu-id="0dc89-125">-namedpipeactivation – aktivační služba pojmenovaného kanálu (nepodporovaná v profilu klienta .NET 4</span><span class="sxs-lookup"><span data-stu-id="0dc89-125">-   namedpipeactivation – Named pipe activation service (unsupported on .NET 4 Client Profile</span></span><br /><span data-ttu-id="0dc89-126">-Služba MsmqActivation – aktivační služba MSMQ (nepodporovaná v profilu klienta .NET 4</span><span class="sxs-lookup"><span data-stu-id="0dc89-126">-   msmqactivation – MSMQ activation service (unsupported on .NET 4 Client Profile</span></span><br /><span data-ttu-id="0dc89-127">-ETW – manifesty trasování událostí ETW (Windows Vista nebo novější)</span><span class="sxs-lookup"><span data-stu-id="0dc89-127">-   etw – ETW event tracing manifests (Windows Vista or later)</span></span>|  
|`-q`|<span data-ttu-id="0dc89-128">Tichý režim (zobrazí se pouze protokolování chyb)</span><span class="sxs-lookup"><span data-stu-id="0dc89-128">Quiet mode (only display error logging)</span></span>|  
|`-v`|<span data-ttu-id="0dc89-129">Podrobný režim.</span><span class="sxs-lookup"><span data-stu-id="0dc89-129">Verbose mode.</span></span>|  
|`-nologo`|<span data-ttu-id="0dc89-130">Potlačí zprávu o autorských právech a bannerech.</span><span class="sxs-lookup"><span data-stu-id="0dc89-130">Suppresses the copyright and banner message.</span></span>|  
|`-?`|<span data-ttu-id="0dc89-131">Zobrazí text v nápovědě.</span><span class="sxs-lookup"><span data-stu-id="0dc89-131">Displays help text</span></span>|  
  
## <a name="fixing-the-fileloadexception-error"></a><span data-ttu-id="0dc89-132">Oprava chyby FileLoadException</span><span class="sxs-lookup"><span data-stu-id="0dc89-132">Fixing the FileLoadException Error</span></span>  
 <span data-ttu-id="0dc89-133">Pokud jste na svém počítači nainstalovali předchozí verze služby WCF, může se `FileLoadFoundException` při spuštění nástroje ServiceModelReg k registraci nové instalace zobrazit chyba.</span><span class="sxs-lookup"><span data-stu-id="0dc89-133">If you installed previous versions of WCF on your machine, you may get a `FileLoadFoundException` error when you run the ServiceModelReg tool to register a new installation.</span></span> <span data-ttu-id="0dc89-134">K tomu může dojít i v případě, že jste ručně odebrali soubory z předchozí instalace, ale ponechali jsme nastavení machine.config beze změny.</span><span class="sxs-lookup"><span data-stu-id="0dc89-134">This can happen even if you have manually removed files from the previous install, but left the machine.config settings intact.</span></span>  
  
 <span data-ttu-id="0dc89-135">Chybová zpráva se podobá následujícímu.</span><span class="sxs-lookup"><span data-stu-id="0dc89-135">The error message is similar to the following.</span></span>  
  
```console  
Error: System.IO.FileLoadException: Could not load file or assembly 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040)  
File name: 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'  
```  
  
 <span data-ttu-id="0dc89-136">Poznamenejte si z chybové zprávy, že sestavení System. ServiceModel verze 2.0.0.0 bylo nainstalováno vydáním verze CTP (Release Customer Technology Preview).</span><span class="sxs-lookup"><span data-stu-id="0dc89-136">You should note from the error message that the System.ServiceModel Version 2.0.0.0 assembly was installed by an early Customer Technology Preview (CTP) release.</span></span> <span data-ttu-id="0dc89-137">Aktuální verze sestavení System. ServiceModel byla uvolněna místo toho 3.0.0.0.</span><span class="sxs-lookup"><span data-stu-id="0dc89-137">The current version of the System.ServiceModel assembly released is 3.0.0.0 instead.</span></span> <span data-ttu-id="0dc89-138">Proto k tomuto problému dochází, když chcete nainstalovat oficiální verzi služby WCF na počítač, na kterém je nainstalovaná verze služby WCF pro starší verzi CTP, ale ne úplně odinstalována.</span><span class="sxs-lookup"><span data-stu-id="0dc89-138">Therefore, this issue is encountered when you want to install the official WCF release on a machine where an early CTP release of WCF was installed, but not completely uninstalled.</span></span>  
  
 <span data-ttu-id="0dc89-139">ServiceModelReg.exe nemůže vyčistit předchozí položky verze, ani nemůže registrovat nové položky verze.</span><span class="sxs-lookup"><span data-stu-id="0dc89-139">ServiceModelReg.exe cannot clean up prior version entries, nor can it register the new version's entries.</span></span> <span data-ttu-id="0dc89-140">Jediným alternativním řešením je ruční úprava machine.config. Tento soubor najdete v následujícím umístění.</span><span class="sxs-lookup"><span data-stu-id="0dc89-140">The only workaround is to manually edit machine.config. You can locate this file at the following location.</span></span>  
  
```console  
%windir%\Microsoft.NET\Framework\v2.0.50727\config\machine.config
```  
  
 <span data-ttu-id="0dc89-141">Pokud používáte WCF na 64m počítači, měli byste také upravit stejný soubor v tomto umístění.</span><span class="sxs-lookup"><span data-stu-id="0dc89-141">If you are running WCF on a 64-bit machine, you should also edit the same file at this location.</span></span>  
  
```console  
%windir%\Microsoft.NET\Framework64\v2.0.50727\config\machine.config
```  
  
 <span data-ttu-id="0dc89-142">Vyhledejte v tomto souboru všechny uzly XML, které odkazují na "System. ServiceModel, Version = 2.0.0.0", odstraňte je a všechny podřízené uzly.</span><span class="sxs-lookup"><span data-stu-id="0dc89-142">Locate any XML nodes in this file that refer to "System.ServiceModel, Version=2.0.0.0", delete them and any child nodes.</span></span> <span data-ttu-id="0dc89-143">Uložte soubor a znovu spusťte ServiceModelReg.exe vyřeší tento problém.</span><span class="sxs-lookup"><span data-stu-id="0dc89-143">Save the file and re-run ServiceModelReg.exe resolves this problem.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="0dc89-144">Příklady</span><span class="sxs-lookup"><span data-stu-id="0dc89-144">Examples</span></span>  
 <span data-ttu-id="0dc89-145">Následující příklady ukazují, jak používat nejběžnější možnosti nástroje ServiceModelReg.exe.</span><span class="sxs-lookup"><span data-stu-id="0dc89-145">The following examples show how to use the most common options of the ServiceModelReg.exe tool.</span></span>  
  
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
