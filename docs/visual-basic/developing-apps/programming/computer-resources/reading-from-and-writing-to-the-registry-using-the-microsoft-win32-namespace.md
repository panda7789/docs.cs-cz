---
title: Čtení z registru a zápis do něj s použitím oboru názvů Microsoft.Win32
ms.date: 07/20/2015
helpviewer_keywords:
- registry [Visual Basic]
ms.assetid: 4a0dcce0-c27b-4199-baa8-ee4528da6a56
ms.openlocfilehash: 841344186b8e56717b81e90397aabc608bdc6dab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345488"
---
# <a name="reading-from-and-writing-to-the-registry-using-the-microsoftwin32-namespace-visual-basic"></a><span data-ttu-id="11759-102">Čtení z registru a zápis do něj s použitím oboru názvů Microsoft.Win32 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="11759-102">Reading from and Writing to the Registry Using the Microsoft.Win32 Namespace (Visual Basic)</span></span>

<span data-ttu-id="11759-103">Ačkoli `My.Computer.Registry` by měl y pokrýt základní potřeby při programování <xref:Microsoft.Win32.Registry> <xref:Microsoft.Win32.RegistryKey> proti registru, můžete také použít a třídy v oboru <xref:Microsoft.Win32> názvů rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="11759-103">Although `My.Computer.Registry` should cover your basic needs when programming against the registry, you can also use the <xref:Microsoft.Win32.Registry> and <xref:Microsoft.Win32.RegistryKey> classes in the <xref:Microsoft.Win32> namespace of the .NET Framework.</span></span>  
  
## <a name="keys-in-the-registry-class"></a><span data-ttu-id="11759-104">Klíče ve třídě registru</span><span class="sxs-lookup"><span data-stu-id="11759-104">Keys in the Registry Class</span></span>  

 <span data-ttu-id="11759-105">Třída <xref:Microsoft.Win32.Registry> poskytuje základní klíče registru, které lze použít pro přístup k podklíčům a jejich hodnotám.</span><span class="sxs-lookup"><span data-stu-id="11759-105">The <xref:Microsoft.Win32.Registry> class supplies the base registry keys that can be used to access subkeys and their values.</span></span> <span data-ttu-id="11759-106">Základní klíče samy o sobě jsou jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="11759-106">The base keys themselves are read-only.</span></span> <span data-ttu-id="11759-107">V následující tabulce jsou uvedeny a <xref:Microsoft.Win32.Registry> popsány sedm klíčů vystavených třídou.</span><span class="sxs-lookup"><span data-stu-id="11759-107">The following table lists and describes the seven keys exposed by the <xref:Microsoft.Win32.Registry> class.</span></span>  
  
|<span data-ttu-id="11759-108">**Klíč**</span><span class="sxs-lookup"><span data-stu-id="11759-108">**Key**</span></span>|<span data-ttu-id="11759-109">**Popis**</span><span class="sxs-lookup"><span data-stu-id="11759-109">**Description**</span></span>|  
|-------------|---------------------|  
|<xref:Microsoft.Win32.Registry.ClassesRoot>|<span data-ttu-id="11759-110">Definuje typy dokumentů a vlastnosti přidružené k těmto typům.</span><span class="sxs-lookup"><span data-stu-id="11759-110">Defines the types of documents and the properties associated with those types.</span></span>|  
|<xref:Microsoft.Win32.Registry.CurrentConfig>|<span data-ttu-id="11759-111">Obsahuje informace o konfiguraci hardwaru, které nejsou specifické pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="11759-111">Contains hardware configuration information that is not user-specific.</span></span>|  
|<xref:Microsoft.Win32.Registry.CurrentUser>|<span data-ttu-id="11759-112">Obsahuje informace o aktuálních uživatelských předvolbách, například proměnné prostředí.</span><span class="sxs-lookup"><span data-stu-id="11759-112">Contains information about the current user preferences, such as environmental variables.</span></span>|  
|<xref:Microsoft.Win32.Registry.DynData>|<span data-ttu-id="11759-113">Obsahuje dynamická data registru, například data používaná ovladači virtuálních zařízení.</span><span class="sxs-lookup"><span data-stu-id="11759-113">Contains dynamic registry data, such as that used by Virtual Device Drivers.</span></span>|  
|<xref:Microsoft.Win32.Registry.LocalMachine>|<span data-ttu-id="11759-114">Obsahuje pět podklíčů (hardware, SAM, zabezpečení, software a systém), které obsahují konfigurační data pro místní počítač.</span><span class="sxs-lookup"><span data-stu-id="11759-114">Contains five subkeys (Hardware, SAM, Security, Software, and System) that hold the configuration data for the local computer.</span></span>|  
|<xref:Microsoft.Win32.Registry.PerformanceData>|<span data-ttu-id="11759-115">Obsahuje informace o výkonu softwarových součástí.</span><span class="sxs-lookup"><span data-stu-id="11759-115">Contains performance information for software components.</span></span>|  
|<xref:Microsoft.Win32.Registry.Users>|<span data-ttu-id="11759-116">Obsahuje informace o výchozích uživatelských předvolbách.</span><span class="sxs-lookup"><span data-stu-id="11759-116">Contains information about the default user preferences.</span></span>|  
  
> [!IMPORTANT]
> <span data-ttu-id="11759-117">Je bezpečnější zapisovat data aktuálnímu uživateli (<xref:Microsoft.Win32.Registry.CurrentUser><xref:Microsoft.Win32.Registry.LocalMachine>) než místnímu počítači ( ).</span><span class="sxs-lookup"><span data-stu-id="11759-117">It is more secure to write data to the current user (<xref:Microsoft.Win32.Registry.CurrentUser>) than to the local computer (<xref:Microsoft.Win32.Registry.LocalMachine>).</span></span> <span data-ttu-id="11759-118">Podmínka, která se obvykle označuje jako "squatting" nastane, když klíč, který vytváříte byl dříve vytvořen jiným, možná škodlivý, proces.</span><span class="sxs-lookup"><span data-stu-id="11759-118">A condition that's typically referred to as "squatting" occurs when the key you are creating was previously created by another, possibly malicious, process.</span></span> <span data-ttu-id="11759-119">Chcete-li tomu zabránit, použijte metodu, například <xref:Microsoft.Win32.RegistryKey.GetValue%2A>, která se vrátí, `Nothing` pokud klíč ještě neexistuje.</span><span class="sxs-lookup"><span data-stu-id="11759-119">To prevent this from occurring, use a method, such as <xref:Microsoft.Win32.RegistryKey.GetValue%2A>, that returns `Nothing` if the key does not already exist.</span></span>  
  
## <a name="reading-a-value-from-the-registry"></a><span data-ttu-id="11759-120">Čtení hodnoty z registru</span><span class="sxs-lookup"><span data-stu-id="11759-120">Reading a Value from the Registry</span></span>  

 <span data-ttu-id="11759-121">Následující kód ukazuje, jak číst řetězec z HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="11759-121">The following code shows how to read a string from HKEY_CURRENT_USER.</span></span>  
  
 [!code-vb[VbResourceTasks#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#20)]  
  
 <span data-ttu-id="11759-122">Následující kód čte, přírůstky a pak zapíše řetězec HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="11759-122">The following code reads, increments, and then writes a string to HKEY_CURRENT_USER.</span></span>  
  
 [!code-vb[VbResourceTasks#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="11759-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="11759-123">See also</span></span>

- <xref:System.SystemException>
- <xref:System.ApplicationException>
- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- [<span data-ttu-id="11759-124">Příkaz Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="11759-124">Try...Catch...Finally Statement</span></span>](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="11759-125">Čtení z registru a zápis do něj</span><span class="sxs-lookup"><span data-stu-id="11759-125">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
- [<span data-ttu-id="11759-126">Zabezpečení a registr</span><span class="sxs-lookup"><span data-stu-id="11759-126">Security and the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)
