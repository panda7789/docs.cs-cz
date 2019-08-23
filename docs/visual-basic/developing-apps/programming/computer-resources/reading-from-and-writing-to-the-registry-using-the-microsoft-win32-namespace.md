---
title: Čtení z registru a zápis do něj s použitím oboru názvů Microsoft.Win32 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- registry [Visual Basic]
ms.assetid: 4a0dcce0-c27b-4199-baa8-ee4528da6a56
ms.openlocfilehash: bf0d6ae329c5a09986a4a7bf641fe6820387ff22
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916559"
---
# <a name="reading-from-and-writing-to-the-registry-using-the-microsoftwin32-namespace-visual-basic"></a><span data-ttu-id="cdaab-102">Čtení z registru a zápis do něj s použitím oboru názvů Microsoft.Win32 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cdaab-102">Reading from and Writing to the Registry Using the Microsoft.Win32 Namespace (Visual Basic)</span></span>
<span data-ttu-id="cdaab-103">I `My.Computer.Registry` když by měl pokrývat vaše základní potřeby při programování v registru, můžete také <xref:Microsoft.Win32.Registry> použít třídy <xref:Microsoft.Win32.RegistryKey> a v <xref:Microsoft.Win32> oboru názvů .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cdaab-103">Although `My.Computer.Registry` should cover your basic needs when programming against the registry, you can also use the <xref:Microsoft.Win32.Registry> and <xref:Microsoft.Win32.RegistryKey> classes in the <xref:Microsoft.Win32> namespace of the .NET Framework.</span></span>  
  
## <a name="keys-in-the-registry-class"></a><span data-ttu-id="cdaab-104">Klíče v třídě registru</span><span class="sxs-lookup"><span data-stu-id="cdaab-104">Keys in the Registry Class</span></span>  
 <span data-ttu-id="cdaab-105"><xref:Microsoft.Win32.Registry> Třída poskytuje základní klíče registru, které lze použít pro přístup k podklíčům a jejich hodnotám.</span><span class="sxs-lookup"><span data-stu-id="cdaab-105">The <xref:Microsoft.Win32.Registry> class supplies the base registry keys that can be used to access subkeys and their values.</span></span> <span data-ttu-id="cdaab-106">Základní klíče jsou jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="cdaab-106">The base keys themselves are read-only.</span></span> <span data-ttu-id="cdaab-107">Následující tabulka uvádí a popisuje sedm klíčů vystavených <xref:Microsoft.Win32.Registry> třídou.</span><span class="sxs-lookup"><span data-stu-id="cdaab-107">The following table lists and describes the seven keys exposed by the <xref:Microsoft.Win32.Registry> class.</span></span>  
  
|<span data-ttu-id="cdaab-108">**Key**</span><span class="sxs-lookup"><span data-stu-id="cdaab-108">**Key**</span></span>|<span data-ttu-id="cdaab-109">**Popis**</span><span class="sxs-lookup"><span data-stu-id="cdaab-109">**Description**</span></span>|  
|-------------|---------------------|  
|<xref:Microsoft.Win32.Registry.ClassesRoot>|<span data-ttu-id="cdaab-110">Definuje typy dokumentů a vlastnosti, které jsou k těmto typům přidruženy.</span><span class="sxs-lookup"><span data-stu-id="cdaab-110">Defines the types of documents and the properties associated with those types.</span></span>|  
|<xref:Microsoft.Win32.Registry.CurrentConfig>|<span data-ttu-id="cdaab-111">Obsahuje informace o konfiguraci hardwaru, které nejsou specifické pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="cdaab-111">Contains hardware configuration information that is not user-specific.</span></span>|  
|<xref:Microsoft.Win32.Registry.CurrentUser>|<span data-ttu-id="cdaab-112">Obsahuje informace o uživatelských preferencích, jako jsou proměnné prostředí.</span><span class="sxs-lookup"><span data-stu-id="cdaab-112">Contains information about the current user preferences, such as environmental variables.</span></span>|  
|<xref:Microsoft.Win32.Registry.DynData>|<span data-ttu-id="cdaab-113">Obsahuje dynamická data registru, například ta, která používají ovladače virtuálních zařízení.</span><span class="sxs-lookup"><span data-stu-id="cdaab-113">Contains dynamic registry data, such as that used by Virtual Device Drivers.</span></span>|  
|<xref:Microsoft.Win32.Registry.LocalMachine>|<span data-ttu-id="cdaab-114">Obsahuje pět podklíčů (hardware, SAM, zabezpečení, software a systém), které obsahují konfigurační data pro místní počítač.</span><span class="sxs-lookup"><span data-stu-id="cdaab-114">Contains five subkeys (Hardware, SAM, Security, Software, and System) that hold the configuration data for the local computer.</span></span>|  
|<xref:Microsoft.Win32.Registry.PerformanceData>|<span data-ttu-id="cdaab-115">Obsahuje informace o výkonu pro softwarové součásti.</span><span class="sxs-lookup"><span data-stu-id="cdaab-115">Contains performance information for software components.</span></span>|  
|<xref:Microsoft.Win32.Registry.Users>|<span data-ttu-id="cdaab-116">Obsahuje informace o výchozích uživatelských preferencích.</span><span class="sxs-lookup"><span data-stu-id="cdaab-116">Contains information about the default user preferences.</span></span>|  
  
> [!IMPORTANT]
> <span data-ttu-id="cdaab-117">Je bezpečnější zapsat data do aktuálního uživatele (<xref:Microsoft.Win32.Registry.CurrentUser>) než do místního počítače (<xref:Microsoft.Win32.Registry.LocalMachine>).</span><span class="sxs-lookup"><span data-stu-id="cdaab-117">It is more secure to write data to the current user (<xref:Microsoft.Win32.Registry.CurrentUser>) than to the local computer (<xref:Microsoft.Win32.Registry.LocalMachine>).</span></span> <span data-ttu-id="cdaab-118">Podmínka, která se obvykle označuje jako "squatting", nastane, když se vytvářený klíč dřív vytvořil jiným, možná škodlivým procesem.</span><span class="sxs-lookup"><span data-stu-id="cdaab-118">A condition that's typically referred to as "squatting" occurs when the key you are creating was previously created by another, possibly malicious, process.</span></span> <span data-ttu-id="cdaab-119">Aby k tomu nedošlo, použijte metodu, například <xref:Microsoft.Win32.RegistryKey.GetValue%2A>, která vrátí `Nothing` , pokud klíč ještě neexistuje.</span><span class="sxs-lookup"><span data-stu-id="cdaab-119">To prevent this from occurring, use a method, such as <xref:Microsoft.Win32.RegistryKey.GetValue%2A>, that returns `Nothing` if the key does not already exist.</span></span>  
  
## <a name="reading-a-value-from-the-registry"></a><span data-ttu-id="cdaab-120">Čtení hodnoty z registru</span><span class="sxs-lookup"><span data-stu-id="cdaab-120">Reading a Value from the Registry</span></span>  
 <span data-ttu-id="cdaab-121">Následující kód ukazuje, jak číst řetězec z HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="cdaab-121">The following code shows how to read a string from HKEY_CURRENT_USER.</span></span>  
  
 [!code-vb[VbResourceTasks#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#20)]  
  
 <span data-ttu-id="cdaab-122">Následující kód přečte, zvýší a pak zapíše řetězec do HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="cdaab-122">The following code reads, increments, and then writes a string to HKEY_CURRENT_USER.</span></span>  
  
 [!code-vb[VbResourceTasks#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="cdaab-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cdaab-123">See also</span></span>

- <xref:System.SystemException>
- <xref:System.ApplicationException>
- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- [<span data-ttu-id="cdaab-124">Příkaz Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="cdaab-124">Try...Catch...Finally Statement</span></span>](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="cdaab-125">Čtení z registru a zápis do něj</span><span class="sxs-lookup"><span data-stu-id="cdaab-125">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
- [<span data-ttu-id="cdaab-126">Zabezpečení a registr</span><span class="sxs-lookup"><span data-stu-id="cdaab-126">Security and the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)
