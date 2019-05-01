---
title: Nástroj ServiceModel Registration (ServiceModelReg.exe)
ms.date: 03/30/2017
ms.assetid: 396ec5ae-e34f-4c64-a164-fcf50e86b6ac
ms.openlocfilehash: 5fab1a356cd035ed006bfe90d713e179907e0137
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051777"
---
# <a name="servicemodel-registration-tool-servicemodelregexe"></a><span data-ttu-id="f11bc-102">Nástroj ServiceModel Registration (ServiceModelReg.exe)</span><span class="sxs-lookup"><span data-stu-id="f11bc-102">ServiceModel Registration Tool (ServiceModelReg.exe)</span></span>
<span data-ttu-id="f11bc-103">Tento nástroj příkazového řádku umožňuje spravovat registraci součástí WCF a WF v jednom počítači.</span><span class="sxs-lookup"><span data-stu-id="f11bc-103">This command-line tool provides the ability to manage the registration of WCF and WF components on a single machine.</span></span> <span data-ttu-id="f11bc-104">Za normálních okolností by neměl muset použít tento nástroj jako WCF a WF součásti konfigurují při instalaci.</span><span class="sxs-lookup"><span data-stu-id="f11bc-104">Under normal circumstances you should not need to use this tool as WCF and WF components are configured when installed.</span></span> <span data-ttu-id="f11bc-105">Ale pokud máte problémy s aktivací služby, můžete zkusit k registraci komponenty pomocí tohoto nástroje.</span><span class="sxs-lookup"><span data-stu-id="f11bc-105">But if you are experiencing problems with service activation, you can try to register the components using this tool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f11bc-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f11bc-106">Syntax</span></span>  
  
```  
ServiceModelReg.exe[(-ia|-ua|-r)|((-i|-u) -c:<command>)] [-v|-q] [-nologo] [-?]  
```  
  
## <a name="remarks"></a><span data-ttu-id="f11bc-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f11bc-107">Remarks</span></span>  
 <span data-ttu-id="f11bc-108">Nástroj najdete v následujícím umístění:</span><span class="sxs-lookup"><span data-stu-id="f11bc-108">The tool can be found in the following location:</span></span>  
  
 <span data-ttu-id="f11bc-109">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\\</span><span class="sxs-lookup"><span data-stu-id="f11bc-109">%SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\\</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f11bc-110">Při spuštění nástroje pro registraci ServiceModel [!INCLUDE[wv](../../../includes/wv-md.md)], **funkce Windows** dialogového okna, která nemusí odrážet **aktivace Windows Communication Foundation HTTP** možnost **Rozhraní Microsoft .NET Framework 3.0** zapnutý.</span><span class="sxs-lookup"><span data-stu-id="f11bc-110">When the ServiceModel Registration Tool is run on [!INCLUDE[wv](../../../includes/wv-md.md)], the **Windows Features** dialog may not reflect that the **Windows Communication Foundation HTTP Activation** option under **Microsoft .NET Framework 3.0** is turned on.</span></span> <span data-ttu-id="f11bc-111">**Funkce Windows** dialogového okna můžete dostat kliknutím **Start**, pak klikněte na tlačítko **spustit** a zadáním **OptionalFeatures**.</span><span class="sxs-lookup"><span data-stu-id="f11bc-111">The **Windows Features** dialog can be accessed by clicking **Start**, then click **Run** and then typing **OptionalFeatures**.</span></span>  
  
 <span data-ttu-id="f11bc-112">Následující tabulky popisují požadované možnosti, které lze použít s ServiceModelReg.exe.</span><span class="sxs-lookup"><span data-stu-id="f11bc-112">The following tables describe the options that can be used with ServiceModelReg.exe.</span></span>  
  
|<span data-ttu-id="f11bc-113">Možnost</span><span class="sxs-lookup"><span data-stu-id="f11bc-113">Option</span></span>|<span data-ttu-id="f11bc-114">Popis</span><span class="sxs-lookup"><span data-stu-id="f11bc-114">Description</span></span>|  
|------------|-----------------|  
|`-ia`|<span data-ttu-id="f11bc-115">Nainstaluje všechny komponenty WCF a WF.</span><span class="sxs-lookup"><span data-stu-id="f11bc-115">Installs all WCF and WF components.</span></span>|  
|`-ua`|<span data-ttu-id="f11bc-116">Odinstaluje všechny součásti WCF a WF.</span><span class="sxs-lookup"><span data-stu-id="f11bc-116">Uninstalls all WCF and WF components.</span></span>|  
|`-r`|<span data-ttu-id="f11bc-117">Opraví všechny součásti WCF a WF.</span><span class="sxs-lookup"><span data-stu-id="f11bc-117">Repairs all WCF and WF components.</span></span>|  
|`-i`|<span data-ttu-id="f11bc-118">Nainstaluje součásti WCF a WF zadaným – c.</span><span class="sxs-lookup"><span data-stu-id="f11bc-118">Installs WCF and WF components specified with –c.</span></span>|  
|`-u`|<span data-ttu-id="f11bc-119">Odinstaluje součástí WCF a WF zadaným – c.</span><span class="sxs-lookup"><span data-stu-id="f11bc-119">Uninstalls WCF and WF components specified with –c.</span></span>|  
|`-c`|<span data-ttu-id="f11bc-120">Nainstaluje nebo odinstaluje komponentu:</span><span class="sxs-lookup"><span data-stu-id="f11bc-120">Installs or uninstalls a component:</span></span><br /><br /> <span data-ttu-id="f11bc-121">-httpnamespace – Namespace rezervace protokolu HTTP</span><span class="sxs-lookup"><span data-stu-id="f11bc-121">-   httpnamespace – HTTP Namespace Reservation</span></span><br /><span data-ttu-id="f11bc-122">služby Sdílení portů - tcpportsharing – TCP</span><span class="sxs-lookup"><span data-stu-id="f11bc-122">-   tcpportsharing – TCP port sharing service</span></span><br /><span data-ttu-id="f11bc-123">aktivační služba - tcpactivation – TCP (Nepodporovaná na profil klienta rozhraní .NET 4)</span><span class="sxs-lookup"><span data-stu-id="f11bc-123">-   tcpactivation – TCP activation service (unsupported on .NET 4 Client Profile)</span></span><br /><span data-ttu-id="f11bc-124">služby - namedpipeactivation – aktivace pojmenovaného kanálu (Nepodporovaná na profil klienta rozhraní .NET 4</span><span class="sxs-lookup"><span data-stu-id="f11bc-124">-   namedpipeactivation – Named pipe activation service (unsupported on .NET 4 Client Profile</span></span><br /><span data-ttu-id="f11bc-125">aktivační služba - služba msmqactivation – služby MSMQ (Nepodporovaná na profil klienta rozhraní .NET 4</span><span class="sxs-lookup"><span data-stu-id="f11bc-125">-   msmqactivation – MSMQ activation service (unsupported on .NET 4 Client Profile</span></span><br /><span data-ttu-id="f11bc-126">manifesty trasování událostí trasování událostí pro – Windows – trasování událostí pro Windows (Windows Vista nebo novější)</span><span class="sxs-lookup"><span data-stu-id="f11bc-126">-   etw – ETW event tracing manifests (Windows Vista or later)</span></span>|  
|`-q`|<span data-ttu-id="f11bc-127">Nastaví tichý režim (jenom protokolování zobrazení chyb)</span><span class="sxs-lookup"><span data-stu-id="f11bc-127">Quiet mode (only display error logging)</span></span>|  
|`-v`|<span data-ttu-id="f11bc-128">Režim s komentářem.</span><span class="sxs-lookup"><span data-stu-id="f11bc-128">Verbose mode.</span></span>|  
|`-nologo`|<span data-ttu-id="f11bc-129">Potlačí zprávu o autorských právech a úvodní nápis.</span><span class="sxs-lookup"><span data-stu-id="f11bc-129">Suppresses the copyright and banner message.</span></span>|  
|`-?`|<span data-ttu-id="f11bc-130">Zobrazí text nápovědy</span><span class="sxs-lookup"><span data-stu-id="f11bc-130">Displays help text</span></span>|  
  
## <a name="fixing-the-fileloadexception-error"></a><span data-ttu-id="f11bc-131">Oprava chyby FileLoadException –</span><span class="sxs-lookup"><span data-stu-id="f11bc-131">Fixing the FileLoadException Error</span></span>  
 <span data-ttu-id="f11bc-132">Pokud jste nainstalovali dřívější verze služby WCF na svém počítači, může se zobrazit `FileLoadFoundException` při spuštění nástroje ServiceModelReg zaregistrovat nové instalace došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="f11bc-132">If you installed previous versions of WCF on your machine, you may get a `FileLoadFoundException` error when you run the ServiceModelReg tool to register a new installation.</span></span> <span data-ttu-id="f11bc-133">Může to i v případě, že máte ručně odebrat soubory z předchozí instalace, ale nastavení machine.config zůstává nedotčeno.</span><span class="sxs-lookup"><span data-stu-id="f11bc-133">This can happen even if you have manually removed files from the previous install, but left the machine.config settings intact.</span></span>  
  
 <span data-ttu-id="f11bc-134">Chybová zpráva podobná následující.</span><span class="sxs-lookup"><span data-stu-id="f11bc-134">The error message is similar to the following.</span></span>  
  
```  
Error: System.IO.FileLoadException: Could not load file or assembly 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040)  
File name: 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'  
```  
  
 <span data-ttu-id="f11bc-135">Nezapomeňte přitom z chybové zprávy, že byla nainstalována sestavení verze 2.0.0.0 System.ServiceModel podle raného vydání zákazníka Technology Preview (CTP).</span><span class="sxs-lookup"><span data-stu-id="f11bc-135">You should note from the error message that the System.ServiceModel Version 2.0.0.0 assembly was installed by an early Customer Technology Preview (CTP) release.</span></span> <span data-ttu-id="f11bc-136">Aktuální verze sestavení System.ServiceModel vydání je 3.0.0.0 místo.</span><span class="sxs-lookup"><span data-stu-id="f11bc-136">The current version of the System.ServiceModel assembly released is 3.0.0.0 instead.</span></span> <span data-ttu-id="f11bc-137">Proto se tento problém je došlo při chcete nainstalovat oficiálním vydáním WCF na počítači, kde byla nainstalována dřívější verzi CTP služby WCF, ale není zcela odinstalována.</span><span class="sxs-lookup"><span data-stu-id="f11bc-137">Therefore, this issue is encountered when you want to install the official WCF release on a machine where an early CTP release of WCF was installed, but not completely uninstalled.</span></span>  
  
 <span data-ttu-id="f11bc-138">ServiceModelReg.exe nelze vymazat, starší verze položky ani můžete zaregistrovat nové verze položky.</span><span class="sxs-lookup"><span data-stu-id="f11bc-138">ServiceModelReg.exe cannot clean up prior version entries, nor can it register the new version's entries.</span></span> <span data-ttu-id="f11bc-139">Jediným alternativním řešením je ručně upravit soubor machine.config. Můžete najít tento soubor v následujícím umístění.</span><span class="sxs-lookup"><span data-stu-id="f11bc-139">The only workaround is to manually edit machine.config. You can locate this file at the following location.</span></span>  
  
```  
%windir%\Microsoft.NET\Framework\v2.0.50727\config\machine.config   
```  
  
 <span data-ttu-id="f11bc-140">Pokud používáte WCF na 64bitovém počítači, byste měli upravovat stejný soubor v tomto umístění.</span><span class="sxs-lookup"><span data-stu-id="f11bc-140">If you are running WCF on a 64-bit machine, you should also edit the same file at this location.</span></span>  
  
```  
%windir%\Microsoft.NET\Framework64\v2.0.50727\config\machine.config   
```  
  
 <span data-ttu-id="f11bc-141">Vyhledejte žádnému z uzlů XML v tomto souboru, který najdete "System.ServiceModel, verze = 2.0.0.0", odstraňte je a všechny podřízené uzly.</span><span class="sxs-lookup"><span data-stu-id="f11bc-141">Locate any XML nodes in this file that refer to "System.ServiceModel, Version=2.0.0.0", delete them and any child nodes.</span></span> <span data-ttu-id="f11bc-142">Uložte soubor a znovu spusťte ServiceModelReg.exe Tento problém se vyřeší.</span><span class="sxs-lookup"><span data-stu-id="f11bc-142">Save the file and re-run ServiceModelReg.exe resolves this problem.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="f11bc-143">Příklady</span><span class="sxs-lookup"><span data-stu-id="f11bc-143">Examples</span></span>  
 <span data-ttu-id="f11bc-144">Následující příklady ukazují, jak používat nástroj ServiceModelReg.exe nejběžnější možnosti.</span><span class="sxs-lookup"><span data-stu-id="f11bc-144">The following examples show how to use the most common options of the ServiceModelReg.exe tool.</span></span>  
  
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
