---
title: Nástroj ServiceModel Registration (ServiceModelReg.exe)
ms.date: 03/30/2017
ms.assetid: 396ec5ae-e34f-4c64-a164-fcf50e86b6ac
ms.openlocfilehash: 5fab1a356cd035ed006bfe90d713e179907e0137
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="servicemodel-registration-tool-servicemodelregexe"></a><span data-ttu-id="ae075-102">Nástroj ServiceModel Registration (ServiceModelReg.exe)</span><span class="sxs-lookup"><span data-stu-id="ae075-102">ServiceModel Registration Tool (ServiceModelReg.exe)</span></span>
<span data-ttu-id="ae075-103">Tento nástroj příkazového řádku umožňuje spravovat registraci komponent WCF a WF na jednom počítači.</span><span class="sxs-lookup"><span data-stu-id="ae075-103">This command-line tool provides the ability to manage the registration of WCF and WF components on a single machine.</span></span> <span data-ttu-id="ae075-104">Za normálních podmínek by neměl budete muset použít tento nástroj jako WCF a konfigurace WF součástí při instalaci.</span><span class="sxs-lookup"><span data-stu-id="ae075-104">Under normal circumstances you should not need to use this tool as WCF and WF components are configured when installed.</span></span> <span data-ttu-id="ae075-105">Ale pokud dochází k potížím s aktivací prostřednictvím služby, můžete zkusit k registraci komponenty pomocí tohoto nástroje.</span><span class="sxs-lookup"><span data-stu-id="ae075-105">But if you are experiencing problems with service activation, you can try to register the components using this tool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae075-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ae075-106">Syntax</span></span>  
  
```  
ServiceModelReg.exe[(-ia|-ua|-r)|((-i|-u) -c:<command>)] [-v|-q] [-nologo] [-?]  
```  
  
## <a name="remarks"></a><span data-ttu-id="ae075-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ae075-107">Remarks</span></span>  
 <span data-ttu-id="ae075-108">Tento nástroj naleznete v následujícím umístění:</span><span class="sxs-lookup"><span data-stu-id="ae075-108">The tool can be found in the following location:</span></span>  
  
 <span data-ttu-id="ae075-109">Foundation\ %SystemRoot%\Microsoft.Net\Framework\v3.0\Windows komunikace</span><span class="sxs-lookup"><span data-stu-id="ae075-109">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\\</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ae075-110">Pokud je spuštěn nástroj ServiceModel Registration [!INCLUDE[wv](../../../includes/wv-md.md)], **funkce systému Windows** nemusí odrážet dialogu, který **aktivace Windows Communication Foundation HTTP** možnosti v části **Rozhraní Microsoft .NET Framework 3.0** je zapnutý.</span><span class="sxs-lookup"><span data-stu-id="ae075-110">When the ServiceModel Registration Tool is run on [!INCLUDE[wv](../../../includes/wv-md.md)], the **Windows Features** dialog may not reflect that the **Windows Communication Foundation HTTP Activation** option under **Microsoft .NET Framework 3.0** is turned on.</span></span> <span data-ttu-id="ae075-111">**Funkce systému Windows** dialogové okno můžete dostat kliknutím na **spustit**, pak klikněte na tlačítko **spustit** a zadáním **OptionalFeatures**.</span><span class="sxs-lookup"><span data-stu-id="ae075-111">The **Windows Features** dialog can be accessed by clicking **Start**, then click **Run** and then typing **OptionalFeatures**.</span></span>  
  
 <span data-ttu-id="ae075-112">Následující tabulka popisuje možnosti, které lze použít s ServiceModelReg.exe.</span><span class="sxs-lookup"><span data-stu-id="ae075-112">The following tables describe the options that can be used with ServiceModelReg.exe.</span></span>  
  
|<span data-ttu-id="ae075-113">Možnost</span><span class="sxs-lookup"><span data-stu-id="ae075-113">Option</span></span>|<span data-ttu-id="ae075-114">Popis</span><span class="sxs-lookup"><span data-stu-id="ae075-114">Description</span></span>|  
|------------|-----------------|  
|`-ia`|<span data-ttu-id="ae075-115">Nainstaluje všechny komponenty WCF a WF.</span><span class="sxs-lookup"><span data-stu-id="ae075-115">Installs all WCF and WF components.</span></span>|  
|`-ua`|<span data-ttu-id="ae075-116">Odinstaluje všechny součásti WCF a WF.</span><span class="sxs-lookup"><span data-stu-id="ae075-116">Uninstalls all WCF and WF components.</span></span>|  
|`-r`|<span data-ttu-id="ae075-117">Opraví všechny součásti WCF a WF.</span><span class="sxs-lookup"><span data-stu-id="ae075-117">Repairs all WCF and WF components.</span></span>|  
|`-i`|<span data-ttu-id="ae075-118">Nainstaluje komponenty WCF a WF zadaným – c.</span><span class="sxs-lookup"><span data-stu-id="ae075-118">Installs WCF and WF components specified with –c.</span></span>|  
|`-u`|<span data-ttu-id="ae075-119">Odinstaluje součásti WCF a WF zadaným – c.</span><span class="sxs-lookup"><span data-stu-id="ae075-119">Uninstalls WCF and WF components specified with –c.</span></span>|  
|`-c`|<span data-ttu-id="ae075-120">Instaluje a odinstaluje součásti:</span><span class="sxs-lookup"><span data-stu-id="ae075-120">Installs or uninstalls a component:</span></span><br /><br /> <span data-ttu-id="ae075-121">-httpnamespace – Namespace rezervaci protokolu HTTP</span><span class="sxs-lookup"><span data-stu-id="ae075-121">-   httpnamespace – HTTP Namespace Reservation</span></span><br /><span data-ttu-id="ae075-122">služby Sdílení portů - tcpportsharing – TCP</span><span class="sxs-lookup"><span data-stu-id="ae075-122">-   tcpportsharing – TCP port sharing service</span></span><br /><span data-ttu-id="ae075-123">aktivační služba - tcpactivation – TCP (nepodporovaný profil klienta rozhraní .NET 4)</span><span class="sxs-lookup"><span data-stu-id="ae075-123">-   tcpactivation – TCP activation service (unsupported on .NET 4 Client Profile)</span></span><br /><span data-ttu-id="ae075-124">služby - namedpipeactivation – pojmenovaný kanál aktivace (nepodporovaný profil klienta rozhraní .NET 4</span><span class="sxs-lookup"><span data-stu-id="ae075-124">-   namedpipeactivation – Named pipe activation service (unsupported on .NET 4 Client Profile</span></span><br /><span data-ttu-id="ae075-125">aktivační služba - služba msmqactivation – služby MSMQ (nepodporovaný profil klienta rozhraní .NET 4</span><span class="sxs-lookup"><span data-stu-id="ae075-125">-   msmqactivation – MSMQ activation service (unsupported on .NET 4 Client Profile</span></span><br /><span data-ttu-id="ae075-126">manifesty trasování událostí - etw – trasování událostí pro Windows (Windows Vista nebo novější)</span><span class="sxs-lookup"><span data-stu-id="ae075-126">-   etw – ETW event tracing manifests (Windows Vista or later)</span></span>|  
|`-q`|<span data-ttu-id="ae075-127">Tichý režim (jenom protokolování chyb zobrazení)</span><span class="sxs-lookup"><span data-stu-id="ae075-127">Quiet mode (only display error logging)</span></span>|  
|`-v`|<span data-ttu-id="ae075-128">Podrobné režimu.</span><span class="sxs-lookup"><span data-stu-id="ae075-128">Verbose mode.</span></span>|  
|`-nologo`|<span data-ttu-id="ae075-129">Potlačí zprávu o autorských právech a hlavičku.</span><span class="sxs-lookup"><span data-stu-id="ae075-129">Suppresses the copyright and banner message.</span></span>|  
|`-?`|<span data-ttu-id="ae075-130">Zobrazí text nápovědy</span><span class="sxs-lookup"><span data-stu-id="ae075-130">Displays help text</span></span>|  
  
## <a name="fixing-the-fileloadexception-error"></a><span data-ttu-id="ae075-131">Oprava chyby FileLoadException</span><span class="sxs-lookup"><span data-stu-id="ae075-131">Fixing the FileLoadException Error</span></span>  
 <span data-ttu-id="ae075-132">Pokud jste nainstalovali předchozí verze služby WCF na počítači, může dojít `FileLoadFoundException` při spuštění nástroje ServiceModelReg zaregistrovat nové instalace došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="ae075-132">If you installed previous versions of WCF on your machine, you may get a `FileLoadFoundException` error when you run the ServiceModelReg tool to register a new installation.</span></span> <span data-ttu-id="ae075-133">Tomu může dojít i v případě, že máte ručně odebrat soubory z předchozí instalace, ale zůstává nedotčeno nastavení souboru machine.config.</span><span class="sxs-lookup"><span data-stu-id="ae075-133">This can happen even if you have manually removed files from the previous install, but left the machine.config settings intact.</span></span>  
  
 <span data-ttu-id="ae075-134">Chybová zpráva je podobný následujícímu.</span><span class="sxs-lookup"><span data-stu-id="ae075-134">The error message is similar to the following.</span></span>  
  
```  
Error: System.IO.FileLoadException: Could not load file or assembly 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040)  
File name: 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'  
```  
  
 <span data-ttu-id="ae075-135">Nezapomeňte přitom z chybová zpráva, že byl nainstalován System.ServiceModel verzi 2.0.0.0 sestavení pomocí předběžnou verzi zákazníka Technology Preview (CTP).</span><span class="sxs-lookup"><span data-stu-id="ae075-135">You should note from the error message that the System.ServiceModel Version 2.0.0.0 assembly was installed by an early Customer Technology Preview (CTP) release.</span></span> <span data-ttu-id="ae075-136">Aktuální verze sestavení System.ServiceModel vydané 3.0.0.0 se místo toho.</span><span class="sxs-lookup"><span data-stu-id="ae075-136">The current version of the System.ServiceModel assembly released is 3.0.0.0 instead.</span></span> <span data-ttu-id="ae075-137">Tento problém je tedy došlo, pokud chcete nainstalovat oficiální verzi WCF na počítači, kde byla předběžnou verzi CTP WCF nainstalovaná, ale není zcela odinstalována.</span><span class="sxs-lookup"><span data-stu-id="ae075-137">Therefore, this issue is encountered when you want to install the official WCF release on a machine where an early CTP release of WCF was installed, but not completely uninstalled.</span></span>  
  
 <span data-ttu-id="ae075-138">ServiceModelReg.exe nelze vyčistit předchozí verze položky, ani můžete zaregistrovat na novou verzi položky.</span><span class="sxs-lookup"><span data-stu-id="ae075-138">ServiceModelReg.exe cannot clean up prior version entries, nor can it register the new version's entries.</span></span> <span data-ttu-id="ae075-139">Jediným řešením je ruční úpravy souboru machine.config. Tento soubor v následujícím umístění lze vyhledat.</span><span class="sxs-lookup"><span data-stu-id="ae075-139">The only workaround is to manually edit machine.config. You can locate this file at the following location.</span></span>  
  
```  
%windir%\Microsoft.NET\Framework\v2.0.50727\config\machine.config   
```  
  
 <span data-ttu-id="ae075-140">Pokud používáte WCF na 64bitový počítač, by také upravit stejný soubor v tomto umístění.</span><span class="sxs-lookup"><span data-stu-id="ae075-140">If you are running WCF on a 64-bit machine, you should also edit the same file at this location.</span></span>  
  
```  
%windir%\Microsoft.NET\Framework64\v2.0.50727\config\machine.config   
```  
  
 <span data-ttu-id="ae075-141">Vyhledejte žádnému z uzlů XML v tomto souboru, který najdete "System.ServiceModel, verze = 2.0.0.0", odstraňte je a všechny podřízené uzly.</span><span class="sxs-lookup"><span data-stu-id="ae075-141">Locate any XML nodes in this file that refer to "System.ServiceModel, Version=2.0.0.0", delete them and any child nodes.</span></span> <span data-ttu-id="ae075-142">Uložte tento soubor a znovu spusťte ServiceModelReg.exe Tento problém se vyřeší.</span><span class="sxs-lookup"><span data-stu-id="ae075-142">Save the file and re-run ServiceModelReg.exe resolves this problem.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="ae075-143">Příklady</span><span class="sxs-lookup"><span data-stu-id="ae075-143">Examples</span></span>  
 <span data-ttu-id="ae075-144">Následující příklady ukazují, jak používat nástroj ServiceModelReg.exe nejběžnější možnosti.</span><span class="sxs-lookup"><span data-stu-id="ae075-144">The following examples show how to use the most common options of the ServiceModelReg.exe tool.</span></span>  
  
```  
ServiceModelReg.exe -ia  
  Installs all components  
ServiceModelReg.exe -i -c:httpnamespace -c:etw  
  Installs HTTP namespace reservation and ETW manifests  
ServiceModelReg.exe -u -c:etw  
  Uninstalls ETW manifests  
ServiceModelReg.exe -r  
  Repairs an extended install  
```
