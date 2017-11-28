---
title: "Čtení z registru a zápis do něj s použitím oboru názvů Microsoft.Win32 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: registry [Visual Basic]
ms.assetid: 4a0dcce0-c27b-4199-baa8-ee4528da6a56
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 462cc5c3854035cfc04c7c5df6905c2cfbd486ed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="reading-from-and-writing-to-the-registry-using-the-microsoftwin32-namespace-visual-basic"></a><span data-ttu-id="d3aa2-102">Čtení z registru a zápis do něj s použitím oboru názvů Microsoft.Win32 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d3aa2-102">Reading from and Writing to the Registry Using the Microsoft.Win32 Namespace (Visual Basic)</span></span>
<span data-ttu-id="d3aa2-103">I když `My.Computer.Registry` by měla zahrnovat základní potřeb při programové ošetření registru, můžete také použít <xref:Microsoft.Win32.Registry> a <xref:Microsoft.Win32.RegistryKey> třídy v <xref:Microsoft.Win32> obor názvů [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d3aa2-103">Although `My.Computer.Registry` should cover your basic needs when programming against the registry, you can also use the <xref:Microsoft.Win32.Registry> and <xref:Microsoft.Win32.RegistryKey> classes in the <xref:Microsoft.Win32> namespace of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span>  
  
## <a name="keys-in-the-registry-class"></a><span data-ttu-id="d3aa2-104">Klíče v registru – třída</span><span class="sxs-lookup"><span data-stu-id="d3aa2-104">Keys in the Registry Class</span></span>  
 <span data-ttu-id="d3aa2-105"><xref:Microsoft.Win32.Registry> Třída poskytuje základní registru klíčů, které lze použít pro přístup k podklíče a jejich hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d3aa2-105">The <xref:Microsoft.Win32.Registry> class supplies the base registry keys that can be used to access subkeys and their values.</span></span> <span data-ttu-id="d3aa2-106">Základní klíče jsou jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="d3aa2-106">The base keys themselves are read-only.</span></span> <span data-ttu-id="d3aa2-107">Následující tabulka uvádí a popisuje sedm klíčů vystavené <xref:Microsoft.Win32.Registry> třídy.</span><span class="sxs-lookup"><span data-stu-id="d3aa2-107">The following table lists and describes the seven keys exposed by the <xref:Microsoft.Win32.Registry> class.</span></span>  
  
|<span data-ttu-id="d3aa2-108">**Klíč**</span><span class="sxs-lookup"><span data-stu-id="d3aa2-108">**Key**</span></span>|<span data-ttu-id="d3aa2-109">**Popis**</span><span class="sxs-lookup"><span data-stu-id="d3aa2-109">**Description**</span></span>|  
|-------------|---------------------|  
|<xref:Microsoft.Win32.Registry.ClassesRoot>|<span data-ttu-id="d3aa2-110">Definuje typy dokumentů a vlastnosti související s těmito typy.</span><span class="sxs-lookup"><span data-stu-id="d3aa2-110">Defines the types of documents and the properties associated with those types.</span></span>|  
|<xref:Microsoft.Win32.Registry.CurrentConfig>|<span data-ttu-id="d3aa2-111">Obsahuje informace o konfiguraci hardwaru, které nejsou specifické pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="d3aa2-111">Contains hardware configuration information that is not user-specific.</span></span>|  
|<xref:Microsoft.Win32.Registry.CurrentUser>|<span data-ttu-id="d3aa2-112">Obsahuje informace o aktuální uživatelské předvolby, například proměnné prostředí.</span><span class="sxs-lookup"><span data-stu-id="d3aa2-112">Contains information about the current user preferences, such as environmental variables.</span></span>|  
|<xref:Microsoft.Win32.Registry.DynData>|<span data-ttu-id="d3aa2-113">Obsahuje dynamické registru data, jako je například použité virtuální ovladače zařízení.</span><span class="sxs-lookup"><span data-stu-id="d3aa2-113">Contains dynamic registry data, such as that used by Virtual Device Drivers.</span></span>|  
|<xref:Microsoft.Win32.Registry.LocalMachine>|<span data-ttu-id="d3aa2-114">Obsahuje pět podklíčů (Hardware, SAM, zabezpečení, softwaru a systému), které obsahují konfigurační data pro místní počítač.</span><span class="sxs-lookup"><span data-stu-id="d3aa2-114">Contains five subkeys (Hardware, SAM, Security, Software, and System) that hold the configuration data for the local computer.</span></span>|  
|<xref:Microsoft.Win32.Registry.PerformanceData>|<span data-ttu-id="d3aa2-115">Obsahuje informace o výkonu pro softwarové součásti.</span><span class="sxs-lookup"><span data-stu-id="d3aa2-115">Contains performance information for software components.</span></span>|  
|<xref:Microsoft.Win32.Registry.Users>|<span data-ttu-id="d3aa2-116">Obsahuje informace o uživatelských předvoleb výchozí.</span><span class="sxs-lookup"><span data-stu-id="d3aa2-116">Contains information about the default user preferences.</span></span>|  
  
> [!IMPORTANT]
>  <span data-ttu-id="d3aa2-117">Je bezpečnější zapsat data do aktuální uživatel (<xref:Microsoft.Win32.Registry.CurrentUser>) než k místnímu počítači (<xref:Microsoft.Win32.Registry.LocalMachine>).</span><span class="sxs-lookup"><span data-stu-id="d3aa2-117">It is more secure to write data to the current user (<xref:Microsoft.Win32.Registry.CurrentUser>) than to the local computer (<xref:Microsoft.Win32.Registry.LocalMachine>).</span></span> <span data-ttu-id="d3aa2-118">Podmínku, která se obvykle označuje jako "obsazení" nastane, když klíč, který vytváříte byl dříve vytvořen v jiné, potenciálně škodlivý, procesu.</span><span class="sxs-lookup"><span data-stu-id="d3aa2-118">A condition that's typically referred to as "squatting" occurs when the key you are creating was previously created by another, possibly malicious, process.</span></span> <span data-ttu-id="d3aa2-119">Chcete-li tomu zabránit, použijte metodu, jako například <xref:Microsoft.Win32.RegistryKey.GetValue%2A>, který vrátí `Nothing` Pokud klíč ještě neexistuje.</span><span class="sxs-lookup"><span data-stu-id="d3aa2-119">To prevent this from occurring, use a method, such as <xref:Microsoft.Win32.RegistryKey.GetValue%2A>, that returns `Nothing` if the key does not already exist.</span></span>  
  
## <a name="reading-a-value-from-the-registry"></a><span data-ttu-id="d3aa2-120">Čtení hodnoty z registru</span><span class="sxs-lookup"><span data-stu-id="d3aa2-120">Reading a Value from the Registry</span></span>  
 <span data-ttu-id="d3aa2-121">Následující kód ukazuje, jak číst řetězce z HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="d3aa2-121">The following code shows how to read a string from HKEY_CURRENT_USER.</span></span>  
  
 [!code-vb[VbResourceTasks#20](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/reading-from-and-writing-to-the-registry-using-the-microsoft-win32-namespace_1.vb)]  
  
 <span data-ttu-id="d3aa2-122">Následující kód čte, se zvýší a pak zapíše řetězec do HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="d3aa2-122">The following code reads, increments, and then writes a string to HKEY_CURRENT_USER.</span></span>  
  
 [!code-vb[VbResourceTasks#21](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/reading-from-and-writing-to-the-registry-using-the-microsoft-win32-namespace_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="d3aa2-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="d3aa2-123">See Also</span></span>  
 <xref:System.SystemException>  
 <xref:System.ApplicationException>  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>  
 [<span data-ttu-id="d3aa2-124">Try... Catch... Finally – příkaz</span><span class="sxs-lookup"><span data-stu-id="d3aa2-124">Try...Catch...Finally Statement</span></span>](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [<span data-ttu-id="d3aa2-125">Čtení a zápis do registru</span><span class="sxs-lookup"><span data-stu-id="d3aa2-125">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)  
 [<span data-ttu-id="d3aa2-126">Zabezpečení a registr</span><span class="sxs-lookup"><span data-stu-id="d3aa2-126">Security and the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)
