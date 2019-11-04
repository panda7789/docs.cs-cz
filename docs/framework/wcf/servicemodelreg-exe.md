---
title: Nástroj ServiceModel Registration (ServiceModelReg.exe)
ms.date: 03/30/2017
ms.assetid: 396ec5ae-e34f-4c64-a164-fcf50e86b6ac
ms.openlocfilehash: aa9fc1b2338007db240fb10a9af35754107b07d0
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424878"
---
# <a name="servicemodel-registration-tool-servicemodelregexe"></a><span data-ttu-id="137b3-102">Nástroj ServiceModel Registration (ServiceModelReg.exe)</span><span class="sxs-lookup"><span data-stu-id="137b3-102">ServiceModel Registration Tool (ServiceModelReg.exe)</span></span>
<span data-ttu-id="137b3-103">Tento nástroj příkazového řádku poskytuje možnost spravovat registraci komponent WCF a WF na jednom počítači.</span><span class="sxs-lookup"><span data-stu-id="137b3-103">This command-line tool provides the ability to manage the registration of WCF and WF components on a single machine.</span></span> <span data-ttu-id="137b3-104">Za normálních okolností byste neměli tento nástroj používat, protože komponenty technologie WCF a WF se nakonfigurují po instalaci.</span><span class="sxs-lookup"><span data-stu-id="137b3-104">Under normal circumstances you should not need to use this tool as WCF and WF components are configured when installed.</span></span> <span data-ttu-id="137b3-105">Pokud ale máte problémy s aktivací služby, můžete se pokusit zaregistrovat komponenty pomocí tohoto nástroje.</span><span class="sxs-lookup"><span data-stu-id="137b3-105">But if you are experiencing problems with service activation, you can try to register the components using this tool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="137b3-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="137b3-106">Syntax</span></span>  
  
```console  
ServiceModelReg.exe[(-ia|-ua|-r)|((-i|-u) -c:<command>)] [-v|-q] [-nologo] [-?]  
```  
  
## <a name="remarks"></a><span data-ttu-id="137b3-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="137b3-107">Remarks</span></span>  
 <span data-ttu-id="137b3-108">Nástroj najdete v následujícím umístění:</span><span class="sxs-lookup"><span data-stu-id="137b3-108">The tool can be found in the following location:</span></span>  
  
 <span data-ttu-id="137b3-109">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation </span><span class="sxs-lookup"><span data-stu-id="137b3-109">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation</span></span>\  
  
> [!NOTE]
> <span data-ttu-id="137b3-110">Pokud je nástroj pro registraci ServiceModel spuštěný na [!INCLUDE[wv](../../../includes/wv-md.md)], dialogové okno **funkce systému Windows** nemusí odrážet možnost **Windows Communication Foundation aktivace protokolem HTTP** v rámci **Microsoft .NET Framework 3,0** je zapnutá.</span><span class="sxs-lookup"><span data-stu-id="137b3-110">When the ServiceModel Registration Tool is run on [!INCLUDE[wv](../../../includes/wv-md.md)], the **Windows Features** dialog may not reflect that the **Windows Communication Foundation HTTP Activation** option under **Microsoft .NET Framework 3.0** is turned on.</span></span> <span data-ttu-id="137b3-111">K dialogovému oknu **funkcí Windows** se dostanete tak, že kliknete na **Start**, pak na **Spustit** a pak zadáte **optionalfeatures**.</span><span class="sxs-lookup"><span data-stu-id="137b3-111">The **Windows Features** dialog can be accessed by clicking **Start**, then click **Run** and then typing **OptionalFeatures**.</span></span>  
  
 <span data-ttu-id="137b3-112">V následujících tabulkách jsou popsány možnosti, které lze použít s ServiceModelReg. exe.</span><span class="sxs-lookup"><span data-stu-id="137b3-112">The following tables describe the options that can be used with ServiceModelReg.exe.</span></span>  
  
|<span data-ttu-id="137b3-113">Možnost</span><span class="sxs-lookup"><span data-stu-id="137b3-113">Option</span></span>|<span data-ttu-id="137b3-114">Popis</span><span class="sxs-lookup"><span data-stu-id="137b3-114">Description</span></span>|  
|------------|-----------------|  
|`-ia`|<span data-ttu-id="137b3-115">Nainstaluje všechny součásti WCF a WF.</span><span class="sxs-lookup"><span data-stu-id="137b3-115">Installs all WCF and WF components.</span></span>|  
|`-ua`|<span data-ttu-id="137b3-116">Odinstaluje všechny součásti WCF a WF.</span><span class="sxs-lookup"><span data-stu-id="137b3-116">Uninstalls all WCF and WF components.</span></span>|  
|`-r`|<span data-ttu-id="137b3-117">Opraví všechny součásti WCF a WF.</span><span class="sxs-lookup"><span data-stu-id="137b3-117">Repairs all WCF and WF components.</span></span>|  
|`-i`|<span data-ttu-id="137b3-118">Nainstaluje WCF a součásti WF zadané pomocí – c.</span><span class="sxs-lookup"><span data-stu-id="137b3-118">Installs WCF and WF components specified with –c.</span></span>|  
|`-u`|<span data-ttu-id="137b3-119">Odinstaluje komponenty WCF a WF zadané pomocí – c.</span><span class="sxs-lookup"><span data-stu-id="137b3-119">Uninstalls WCF and WF components specified with –c.</span></span>|  
|`-c`|<span data-ttu-id="137b3-120">Nainstaluje nebo odinstaluje součást:</span><span class="sxs-lookup"><span data-stu-id="137b3-120">Installs or uninstalls a component:</span></span><br /><br /> <span data-ttu-id="137b3-121">-httpnamespace – rezervace oboru názvů HTTP</span><span class="sxs-lookup"><span data-stu-id="137b3-121">-   httpnamespace – HTTP Namespace Reservation</span></span><br /><span data-ttu-id="137b3-122">-tcpportsharing – služba sdílení portů TCP</span><span class="sxs-lookup"><span data-stu-id="137b3-122">-   tcpportsharing – TCP port sharing service</span></span><br /><span data-ttu-id="137b3-123">-tcpactivation – aktivační služba TCP (nepodporovaná v profilu klienta .NET 4)</span><span class="sxs-lookup"><span data-stu-id="137b3-123">-   tcpactivation – TCP activation service (unsupported on .NET 4 Client Profile)</span></span><br /><span data-ttu-id="137b3-124">-namedpipeactivation – aktivační služba pojmenovaného kanálu (nepodporovaná v profilu klienta .NET 4</span><span class="sxs-lookup"><span data-stu-id="137b3-124">-   namedpipeactivation – Named pipe activation service (unsupported on .NET 4 Client Profile</span></span><br /><span data-ttu-id="137b3-125">-Služba MsmqActivation – aktivační služba MSMQ (nepodporovaná v profilu klienta .NET 4</span><span class="sxs-lookup"><span data-stu-id="137b3-125">-   msmqactivation – MSMQ activation service (unsupported on .NET 4 Client Profile</span></span><br /><span data-ttu-id="137b3-126">-ETW – manifesty trasování událostí ETW (Windows Vista nebo novější)</span><span class="sxs-lookup"><span data-stu-id="137b3-126">-   etw – ETW event tracing manifests (Windows Vista or later)</span></span>|  
|`-q`|<span data-ttu-id="137b3-127">Tichý režim (zobrazí se pouze protokolování chyb)</span><span class="sxs-lookup"><span data-stu-id="137b3-127">Quiet mode (only display error logging)</span></span>|  
|`-v`|<span data-ttu-id="137b3-128">Podrobný režim.</span><span class="sxs-lookup"><span data-stu-id="137b3-128">Verbose mode.</span></span>|  
|`-nologo`|<span data-ttu-id="137b3-129">Potlačí zprávu o autorských právech a bannerech.</span><span class="sxs-lookup"><span data-stu-id="137b3-129">Suppresses the copyright and banner message.</span></span>|  
|`-?`|<span data-ttu-id="137b3-130">Zobrazí text v nápovědě.</span><span class="sxs-lookup"><span data-stu-id="137b3-130">Displays help text</span></span>|  
  
## <a name="fixing-the-fileloadexception-error"></a><span data-ttu-id="137b3-131">Oprava chyby FileLoadException</span><span class="sxs-lookup"><span data-stu-id="137b3-131">Fixing the FileLoadException Error</span></span>  
 <span data-ttu-id="137b3-132">Pokud jste na svém počítači nainstalovali předchozí verze služby WCF, může se při spuštění nástroje ServiceModelReg k registraci nové instalace zobrazit chyba `FileLoadFoundException`.</span><span class="sxs-lookup"><span data-stu-id="137b3-132">If you installed previous versions of WCF on your machine, you may get a `FileLoadFoundException` error when you run the ServiceModelReg tool to register a new installation.</span></span> <span data-ttu-id="137b3-133">K tomu může dojít i v případě, že jste ručně odebrali soubory z předchozí instalace, ale ponechali jste nastavení Machine. config beze změny.</span><span class="sxs-lookup"><span data-stu-id="137b3-133">This can happen even if you have manually removed files from the previous install, but left the machine.config settings intact.</span></span>  
  
 <span data-ttu-id="137b3-134">Chybová zpráva se podobá následujícímu.</span><span class="sxs-lookup"><span data-stu-id="137b3-134">The error message is similar to the following.</span></span>  
  
```console  
Error: System.IO.FileLoadException: Could not load file or assembly 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040)  
File name: 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'  
```  
  
 <span data-ttu-id="137b3-135">Poznamenejte si z chybové zprávy, že sestavení System. ServiceModel verze 2.0.0.0 bylo nainstalováno vydáním verze CTP (Release Customer Technology Preview).</span><span class="sxs-lookup"><span data-stu-id="137b3-135">You should note from the error message that the System.ServiceModel Version 2.0.0.0 assembly was installed by an early Customer Technology Preview (CTP) release.</span></span> <span data-ttu-id="137b3-136">Aktuální verze sestavení System. ServiceModel byla uvolněna místo toho 3.0.0.0.</span><span class="sxs-lookup"><span data-stu-id="137b3-136">The current version of the System.ServiceModel assembly released is 3.0.0.0 instead.</span></span> <span data-ttu-id="137b3-137">Proto k tomuto problému dochází, když chcete nainstalovat oficiální verzi služby WCF na počítač, na kterém je nainstalovaná verze služby WCF pro starší verzi CTP, ale ne úplně odinstalována.</span><span class="sxs-lookup"><span data-stu-id="137b3-137">Therefore, this issue is encountered when you want to install the official WCF release on a machine where an early CTP release of WCF was installed, but not completely uninstalled.</span></span>  
  
 <span data-ttu-id="137b3-138">ServiceModelReg. exe nemůže vyčistit předchozí položky verze, ani nemůže registrovat nové položky verze.</span><span class="sxs-lookup"><span data-stu-id="137b3-138">ServiceModelReg.exe cannot clean up prior version entries, nor can it register the new version's entries.</span></span> <span data-ttu-id="137b3-139">Jediným alternativním řešením je ruční úprava souboru Machine. config. Tento soubor najdete v následujícím umístění.</span><span class="sxs-lookup"><span data-stu-id="137b3-139">The only workaround is to manually edit machine.config. You can locate this file at the following location.</span></span>  
  
```console  
%windir%\Microsoft.NET\Framework\v2.0.50727\config\machine.config   
```  
  
 <span data-ttu-id="137b3-140">Pokud používáte WCF na 64m počítači, měli byste také upravit stejný soubor v tomto umístění.</span><span class="sxs-lookup"><span data-stu-id="137b3-140">If you are running WCF on a 64-bit machine, you should also edit the same file at this location.</span></span>  
  
```console  
%windir%\Microsoft.NET\Framework64\v2.0.50727\config\machine.config   
```  
  
 <span data-ttu-id="137b3-141">Vyhledejte v tomto souboru všechny uzly XML, které odkazují na "System. ServiceModel, Version = 2.0.0.0", odstraňte je a všechny podřízené uzly.</span><span class="sxs-lookup"><span data-stu-id="137b3-141">Locate any XML nodes in this file that refer to "System.ServiceModel, Version=2.0.0.0", delete them and any child nodes.</span></span> <span data-ttu-id="137b3-142">Uložte soubor a znovu spusťte ServiceModelReg. exe. Tento problém se vyřeší.</span><span class="sxs-lookup"><span data-stu-id="137b3-142">Save the file and re-run ServiceModelReg.exe resolves this problem.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="137b3-143">Příklady</span><span class="sxs-lookup"><span data-stu-id="137b3-143">Examples</span></span>  
 <span data-ttu-id="137b3-144">Následující příklady ukazují, jak používat nejběžnější možnosti nástroje ServiceModelReg. exe.</span><span class="sxs-lookup"><span data-stu-id="137b3-144">The following examples show how to use the most common options of the ServiceModelReg.exe tool.</span></span>  
  
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
