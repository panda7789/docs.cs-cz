---
title: Použití standardních typů výjimek
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- throwing exceptions, standard types
- catching exceptions
- exceptions, catching
- exceptions, throwing
ms.assetid: ab22ce03-78f9-4dca-8824-c7ed3bdccc27
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9ea4a61be3a76c30c564cbf98ba3318fc6c3e7d4
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47088084"
---
# <a name="using-standard-exception-types"></a>Použití standardních typů výjimek
Tato část popisuje standardních výjimek poskytované rozhraní Framework a podrobnosti o jejich využití. V seznamu nejsou v žádném smyslu vyčerpávající. Najdete na referenční dokumentaci rozhraní .NET Framework pro použití jiných typů výjimek Framework.  
  
## <a name="exception-and-systemexception"></a>Výjimky a SystemException  
 **X DO NOT** throw <xref:System.Exception?displayProperty=nameWithType> nebo <xref:System.SystemException?displayProperty=nameWithType>.  
  
 **X DO NOT** catch `System.Exception` nebo `System.SystemException` v rámci kódu, pokud máte v úmyslu opětovné.  
  
 **X AVOID** zachytávání `System.Exception` nebo `System.SystemException`, kromě obslužné rutiny výjimek nejvyšší úrovně.  
  
## <a name="applicationexception"></a>ApplicationException –  
 **X DO NOT** throw nebo jsou odvozeny od <xref:System.ApplicationException>.  
  
## <a name="invalidoperationexception"></a>InvalidOperationException  
 **✓ DO** throw <xref:System.InvalidOperationException> Pokud objekt je v nevhodném stavu.  
  
## <a name="argumentexception-argumentnullexception-and-argumentoutofrangeexception"></a>ArgumentException ArgumentNullException a ArgumentOutOfRangeException  
 **✓ DO** throw <xref:System.ArgumentException> nebo jednoho z jeho podtypech Pokud chybné argumenty jsou předány na člena. Preferovat nejvíc odvozený typ výjimky, pokud je k dispozici.  
  
 **✓ DO** nastavit `ParamName` při vyvolání jeden podtříd `ArgumentException`.  
  
 Tato vlastnost představuje název parametru, která způsobila vyvolání výjimky. Všimněte si, že vlastnost lze nastavit pomocí jednoho z přetížení konstruktoru.  
  
 **✓ DO** použít `value` pro název implicitní hodnota parametru nastavením vlastností.  
  
## <a name="nullreferenceexception-indexoutofrangeexception-and-accessviolationexception"></a>NullReferenceException IndexOutOfRangeException a výjimka AccessViolationException  
 **X DO NOT** povolit veřejně možné volat rozhraní API pro explicitně nebo implicitně throw <xref:System.NullReferenceException>, <xref:System.AccessViolationException>, nebo <xref:System.IndexOutOfRangeException>. Tyto výjimky jsou vyhrazené a vyvolané prováděcí modul a ve že většině případů označuje chybu.  
  
 Proveďte kontrolu, aby tyto výjimky argumentu. Vyvolání těchto výjimek poskytuje metodu, která se můžou časem změnit podrobnosti implementace.  
  
## <a name="stackoverflowexception"></a>StackOverflowException  
 **X DO NOT** explicitní generování <xref:System.StackOverflowException>. Pouze pomocí modulu CLR by měla být explicitně vyvolána výjimka.  
  
 **X DO NOT** catch `StackOverflowException`.  
  
 Je téměř nemožné psát spravovaný kód, který zůstává konzistentní za přítomnosti libovolného zásobníku přetečení. Díky používání sond přesunout přetečení zásobníku na jasně definovaných místa, nikoli podle anulování z přetečení zásobníku libovolného zůstaly konzistentní nespravované části modulu CLR.  
  
## <a name="outofmemoryexception"></a>OutOfMemoryException  
 **X DO NOT** explicitní generování <xref:System.OutOfMemoryException>. Tato výjimka je vyvolána pouze infrastrukturou CLR.  
  
## <a name="comexception-sehexception-and-executionengineexception"></a>ComException SEHException – a ExecutionEngineException  
 **X DO NOT** explicitní generování <xref:System.Runtime.InteropServices.COMException>, <xref:System.ExecutionEngineException>, a <xref:System.Runtime.InteropServices.SEHException>. Tyto výjimky jsou vyvolány pouze infrastruktury CLR.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikované 22 Oct 2008, Designing Effective jako části této série Microsoft Windows Development.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)  
- [Pokyny k návrhu pro výjimky](../../../docs/standard/design-guidelines/exceptions.md)
