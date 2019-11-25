---
title: Čtení z registru a zápis do něj s použitím oboru názvů Microsoft.Win32
ms.date: 07/20/2015
helpviewer_keywords:
- registry [Visual Basic]
ms.assetid: 4a0dcce0-c27b-4199-baa8-ee4528da6a56
ms.openlocfilehash: 841344186b8e56717b81e90397aabc608bdc6dab
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345488"
---
# <a name="reading-from-and-writing-to-the-registry-using-the-microsoftwin32-namespace-visual-basic"></a>Čtení z registru a zápis do něj s použitím oboru názvů Microsoft.Win32 (Visual Basic)

Although `My.Computer.Registry` should cover your basic needs when programming against the registry, you can also use the <xref:Microsoft.Win32.Registry> and <xref:Microsoft.Win32.RegistryKey> classes in the <xref:Microsoft.Win32> namespace of the .NET Framework.  
  
## <a name="keys-in-the-registry-class"></a>Keys in the Registry Class  

 The <xref:Microsoft.Win32.Registry> class supplies the base registry keys that can be used to access subkeys and their values. The base keys themselves are read-only. The following table lists and describes the seven keys exposed by the <xref:Microsoft.Win32.Registry> class.  
  
|**Key**|**Popis**|  
|-------------|---------------------|  
|<xref:Microsoft.Win32.Registry.ClassesRoot>|Defines the types of documents and the properties associated with those types.|  
|<xref:Microsoft.Win32.Registry.CurrentConfig>|Contains hardware configuration information that is not user-specific.|  
|<xref:Microsoft.Win32.Registry.CurrentUser>|Contains information about the current user preferences, such as environmental variables.|  
|<xref:Microsoft.Win32.Registry.DynData>|Contains dynamic registry data, such as that used by Virtual Device Drivers.|  
|<xref:Microsoft.Win32.Registry.LocalMachine>|Contains five subkeys (Hardware, SAM, Security, Software, and System) that hold the configuration data for the local computer.|  
|<xref:Microsoft.Win32.Registry.PerformanceData>|Contains performance information for software components.|  
|<xref:Microsoft.Win32.Registry.Users>|Contains information about the default user preferences.|  
  
> [!IMPORTANT]
> It is more secure to write data to the current user (<xref:Microsoft.Win32.Registry.CurrentUser>) than to the local computer (<xref:Microsoft.Win32.Registry.LocalMachine>). A condition that's typically referred to as "squatting" occurs when the key you are creating was previously created by another, possibly malicious, process. To prevent this from occurring, use a method, such as <xref:Microsoft.Win32.RegistryKey.GetValue%2A>, that returns `Nothing` if the key does not already exist.  
  
## <a name="reading-a-value-from-the-registry"></a>Reading a Value from the Registry  

 The following code shows how to read a string from HKEY_CURRENT_USER.  
  
 [!code-vb[VbResourceTasks#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#20)]  
  
 The following code reads, increments, and then writes a string to HKEY_CURRENT_USER.  
  
 [!code-vb[VbResourceTasks#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#21)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.SystemException>
- <xref:System.ApplicationException>
- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- [Příkaz Try...Catch...Finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [Čtení z registru a zápis do něj](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
- [Zabezpečení a registr](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)
