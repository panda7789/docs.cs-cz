---
title: Čtení z registru a zápis do něj s použitím oboru názvů Microsoft.Win32 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- registry [Visual Basic]
ms.assetid: 4a0dcce0-c27b-4199-baa8-ee4528da6a56
ms.openlocfilehash: 9b88257dcdd80c5ec5e81e0c3c20822157907fa5
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56966265"
---
# <a name="reading-from-and-writing-to-the-registry-using-the-microsoftwin32-namespace-visual-basic"></a><span data-ttu-id="9459a-102">Čtení z registru a zápis do něj s použitím oboru názvů Microsoft.Win32 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9459a-102">Reading from and Writing to the Registry Using the Microsoft.Win32 Namespace (Visual Basic)</span></span>
<span data-ttu-id="9459a-103">I když `My.Computer.Registry` by měl zahrnovat základní potřeb při programování proti registru, můžete použít také <xref:Microsoft.Win32.Registry> a <xref:Microsoft.Win32.RegistryKey> tříd v <xref:Microsoft.Win32> obor názvů [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9459a-103">Although `My.Computer.Registry` should cover your basic needs when programming against the registry, you can also use the <xref:Microsoft.Win32.Registry> and <xref:Microsoft.Win32.RegistryKey> classes in the <xref:Microsoft.Win32> namespace of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span>  
  
## <a name="keys-in-the-registry-class"></a><span data-ttu-id="9459a-104">Klíče registru třídy</span><span class="sxs-lookup"><span data-stu-id="9459a-104">Keys in the Registry Class</span></span>  
 <span data-ttu-id="9459a-105"><xref:Microsoft.Win32.Registry> Třída poskytuje základní klíče registrů, které můžete použít pro přístup k podklíče a jejich hodnoty.</span><span class="sxs-lookup"><span data-stu-id="9459a-105">The <xref:Microsoft.Win32.Registry> class supplies the base registry keys that can be used to access subkeys and their values.</span></span> <span data-ttu-id="9459a-106">Základní klíče jsou jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="9459a-106">The base keys themselves are read-only.</span></span> <span data-ttu-id="9459a-107">Následující tabulka uvádí a popisuje sedm klíčů vystavené <xref:Microsoft.Win32.Registry> třídy.</span><span class="sxs-lookup"><span data-stu-id="9459a-107">The following table lists and describes the seven keys exposed by the <xref:Microsoft.Win32.Registry> class.</span></span>  
  
|<span data-ttu-id="9459a-108">**Key**</span><span class="sxs-lookup"><span data-stu-id="9459a-108">**Key**</span></span>|<span data-ttu-id="9459a-109">**Popis**</span><span class="sxs-lookup"><span data-stu-id="9459a-109">**Description**</span></span>|  
|-------------|---------------------|  
|<xref:Microsoft.Win32.Registry.ClassesRoot>|<span data-ttu-id="9459a-110">Definuje typy dokumentů a vlastnosti související s těmito typy.</span><span class="sxs-lookup"><span data-stu-id="9459a-110">Defines the types of documents and the properties associated with those types.</span></span>|  
|<xref:Microsoft.Win32.Registry.CurrentConfig>|<span data-ttu-id="9459a-111">Obsahuje informace o konfiguraci hardwaru, které nejsou specifické pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="9459a-111">Contains hardware configuration information that is not user-specific.</span></span>|  
|<xref:Microsoft.Win32.Registry.CurrentUser>|<span data-ttu-id="9459a-112">Obsahuje informace o aktuální uživatelské předvolby, jako jsou proměnné prostředí.</span><span class="sxs-lookup"><span data-stu-id="9459a-112">Contains information about the current user preferences, such as environmental variables.</span></span>|  
|<xref:Microsoft.Win32.Registry.DynData>|<span data-ttu-id="9459a-113">Obsahuje data dynamické registru, jako je například použít virtuální ovladače zařízení.</span><span class="sxs-lookup"><span data-stu-id="9459a-113">Contains dynamic registry data, such as that used by Virtual Device Drivers.</span></span>|  
|<xref:Microsoft.Win32.Registry.LocalMachine>|<span data-ttu-id="9459a-114">Obsahuje pět podklíče (Hardware, SAM, zabezpečení, softwaru a systém), které obsahují konfigurační data v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="9459a-114">Contains five subkeys (Hardware, SAM, Security, Software, and System) that hold the configuration data for the local computer.</span></span>|  
|<xref:Microsoft.Win32.Registry.PerformanceData>|<span data-ttu-id="9459a-115">Obsahuje informace o výkonu pro softwarové součásti.</span><span class="sxs-lookup"><span data-stu-id="9459a-115">Contains performance information for software components.</span></span>|  
|<xref:Microsoft.Win32.Registry.Users>|<span data-ttu-id="9459a-116">Obsahuje informace o uživatelských předvolbách výchozí.</span><span class="sxs-lookup"><span data-stu-id="9459a-116">Contains information about the default user preferences.</span></span>|  
  
> [!IMPORTANT]
>  <span data-ttu-id="9459a-117">Je bezpečnější zapsat data do aktuálního uživatele (<xref:Microsoft.Win32.Registry.CurrentUser>) než do místního počítače (<xref:Microsoft.Win32.Registry.LocalMachine>).</span><span class="sxs-lookup"><span data-stu-id="9459a-117">It is more secure to write data to the current user (<xref:Microsoft.Win32.Registry.CurrentUser>) than to the local computer (<xref:Microsoft.Win32.Registry.LocalMachine>).</span></span> <span data-ttu-id="9459a-118">Podmínku, která se obvykle označuje jako "obsazení" vyvolá se při vytváření klíče dříve vytvořil jiný, potenciálně škodlivý, proces.</span><span class="sxs-lookup"><span data-stu-id="9459a-118">A condition that's typically referred to as "squatting" occurs when the key you are creating was previously created by another, possibly malicious, process.</span></span> <span data-ttu-id="9459a-119">Chcete-li tomu zabránit, použijte metodu, <xref:Microsoft.Win32.RegistryKey.GetValue%2A>, který vrací `Nothing` Pokud klíč ještě neexistuje.</span><span class="sxs-lookup"><span data-stu-id="9459a-119">To prevent this from occurring, use a method, such as <xref:Microsoft.Win32.RegistryKey.GetValue%2A>, that returns `Nothing` if the key does not already exist.</span></span>  
  
## <a name="reading-a-value-from-the-registry"></a><span data-ttu-id="9459a-120">Čtení hodnoty z registru</span><span class="sxs-lookup"><span data-stu-id="9459a-120">Reading a Value from the Registry</span></span>  
 <span data-ttu-id="9459a-121">Následující kód znázorňuje způsob čtení řetězce z HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="9459a-121">The following code shows how to read a string from HKEY_CURRENT_USER.</span></span>  
  
 [!code-vb[VbResourceTasks#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#20)]  
  
 <span data-ttu-id="9459a-122">Následující kód načte, krocích a pak zapíše řetězec do klíče HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="9459a-122">The following code reads, increments, and then writes a string to HKEY_CURRENT_USER.</span></span>  
  
 [!code-vb[VbResourceTasks#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="9459a-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9459a-123">See also</span></span>
- <xref:System.SystemException>
- <xref:System.ApplicationException>
- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- [<span data-ttu-id="9459a-124">Příkaz Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="9459a-124">Try...Catch...Finally Statement</span></span>](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="9459a-125">Čtení z registru a zápis do něj</span><span class="sxs-lookup"><span data-stu-id="9459a-125">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
- [<span data-ttu-id="9459a-126">Zabezpečení a registr</span><span class="sxs-lookup"><span data-stu-id="9459a-126">Security and the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)
