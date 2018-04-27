---
title: Použití typů standardní výjimky
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- throwing exceptions, standard types
- catching exceptions
- exceptions, catching
- exceptions, throwing
ms.assetid: ab22ce03-78f9-4dca-8824-c7ed3bdccc27
caps.latest.revision: 17
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 54e8b750048a00f7ac2591b464ac4c74cb7591b7
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
---
# <a name="using-standard-exception-types"></a>Použití typů standardní výjimky
Tato část popisuje standardní výjimky poskytované rozhraní a podrobnosti o jejich využití. V seznamu je rozhodně není vyčerpávající. Naleznete na referenční dokumentaci rozhraní .NET Framework pro použití jiných typů výjimek Framework.  
  
## <a name="exception-and-systemexception"></a>A SystemException – výjimka  
 **X nesmí** throw <xref:System.Exception?displayProperty=nameWithType> nebo <xref:System.SystemException?displayProperty=nameWithType>.  
  
 **X nesmí** catch `System.Exception` nebo `System.SystemException` v rámci kódu, pokud máte v úmyslu opětovné.  
  
 **X nepoužívejte** zachytávání `System.Exception` nebo `System.SystemException`, kromě obslužné rutiny výjimek nejvyšší úrovně.  
  
## <a name="applicationexception"></a>ApplicationException –  
 **X nesmí** throw nebo jsou odvozeny od <xref:System.ApplicationException>.  
  
## <a name="invalidoperationexception"></a>InvalidOperationException  
 **PROVEĎTE ✓** throw <xref:System.InvalidOperationException> Pokud objekt je v nevhodném stavu.  
  
## <a name="argumentexception-argumentnullexception-and-argumentoutofrangeexception"></a>ArgumentException – ArgumentNullException a výjimka ArgumentOutOfRangeException  
 **PROVEĎTE ✓** throw <xref:System.ArgumentException> nebo jednoho z jeho podtypech Pokud chybné argumenty jsou předány na člena. Dáváte přednost nejodvozenějších typ výjimky, pokud je k dispozici.  
  
 **PROVEĎTE ✓** nastavit `ParamName` při vyvolání jeden podtříd `ArgumentException`.  
  
 Tato vlastnost představuje název parametru, která způsobila vyvolání výjimky. Všimněte si, že vlastnost lze nastavit pomocí jednoho z přetížení konstruktor.  
  
 **PROVEĎTE ✓** použít `value` pro název implicitní hodnota parametru nastavením vlastností.  
  
## <a name="nullreferenceexception-indexoutofrangeexception-and-accessviolationexception"></a>NullReferenceException IndexOutOfRangeException a AccessViolationException  
 **X nesmí** povolit veřejně možné volat rozhraní API pro explicitně nebo implicitně throw <xref:System.NullReferenceException>, <xref:System.AccessViolationException>, nebo <xref:System.IndexOutOfRangeException>. Tyto výjimky jsou vyhrazené a vyvolané modul provádění a ve že většině případů se jednat o chybu.  
  
 Proveďte kontrolu nechcete-li tyto výjimky argumentu. Vyvolání těchto výjimek zpřístupní podrobnosti implementace vaší metody, které můžou časem změnit.  
  
## <a name="stackoverflowexception"></a>StackOverflowException  
 **X nesmí** explicitní generování <xref:System.StackOverflowException>. Pouze pomocí modulu CLR by měla být explicitně vyvolána výjimka.  
  
 **X nesmí** catch `StackOverflowException`.  
  
 Není možné téměř k zápisu spravovaného kódu, který konzistentní případě přetečení zásobníku libovolný. Nespravované části modulu CLR zůstaly konzistentní s použitím sondy přesunout přetečení zásobníku na dobře definovaný místa, a nikoli zálohování z libovolné zásobníku některé.  
  
## <a name="outofmemoryexception"></a>OutOfMemoryException  
 **X nesmí** explicitní generování <xref:System.OutOfMemoryException>. Tato výjimka je vyvolána pouze pomocí infrastruktury CLR.  
  
## <a name="comexception-sehexception-and-executionengineexception"></a>ComException SEHException – a ExecutionEngineException –  
 **X nesmí** explicitní generování <xref:System.Runtime.InteropServices.COMException>, <xref:System.ExecutionEngineException>, a <xref:System.Runtime.InteropServices.SEHException>. Tyto výjimky se mají být vyvolány pouze infrastruktury CLR.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*  
  
## <a name="see-also"></a>Viz také  
 [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)  
 [Pokyny k návrhu pro výjimky](../../../docs/standard/design-guidelines/exceptions.md)
