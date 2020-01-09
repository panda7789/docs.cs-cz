---
title: Použití standardních typů výjimek
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- throwing exceptions, standard types
- catching exceptions
- exceptions, catching
- exceptions, throwing
ms.assetid: ab22ce03-78f9-4dca-8824-c7ed3bdccc27
ms.openlocfilehash: 6b202d618d9d2216c8998181303250081de6781c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708981"
---
# <a name="using-standard-exception-types"></a>Použití standardních typů výjimek
Tato část popisuje standardní výjimky poskytované rozhraním a podrobnosti o jejich použití. Seznam není úplným způsobem vyčerpávající. Informace o použití jiných typů výjimek rozhraní naleznete v referenční dokumentaci k .NET Framework.  
  
## <a name="exception-and-systemexception"></a>Výjimka a SystemException  
 **X DO NOT** throw <xref:System.Exception?displayProperty=nameWithType> nebo <xref:System.SystemException?displayProperty=nameWithType>.  
  
 **X DO NOT** catch `System.Exception` nebo `System.SystemException` v rámci kódu, pokud máte v úmyslu opětovné.  
  
 **X AVOID** zachytávání `System.Exception` nebo `System.SystemException`, kromě obslužné rutiny výjimek nejvyšší úrovně.  
  
## <a name="applicationexception"></a>ApplicationException  
 **X DO NOT** throw nebo jsou odvozeny od <xref:System.ApplicationException>.  
  
## <a name="invalidoperationexception"></a>InvalidOperationException  
 **✓ DO** throw <xref:System.InvalidOperationException> Pokud objekt je v nevhodném stavu.  
  
## <a name="argumentexception-argumentnullexception-and-argumentoutofrangeexception"></a>ArgumentException, ArgumentNullException a ArgumentOutOfRangeException  
 **✓ DO** throw <xref:System.ArgumentException> nebo jednoho z jeho podtypech Pokud chybné argumenty jsou předány na člena. Preferovat největší odvozený typ výjimky, je-li k dispozici.  
  
 **✓ DO** nastavit `ParamName` při vyvolání jeden podtříd `ArgumentException`.  
  
 Tato vlastnost představuje název parametru, který způsobil výjimku vyvolání výjimky. Všimněte si, že vlastnost může být nastavena pomocí jednoho z přetížení konstruktoru.  
  
 **✓ DO** použít `value` pro název implicitní hodnota parametru nastavením vlastností.  
  
## <a name="nullreferenceexception-indexoutofrangeexception-and-accessviolationexception"></a>NullReferenceException, IndexOutOfRangeException a AccessViolationException –  
 **X DO NOT** povolit veřejně možné volat rozhraní API pro explicitně nebo implicitně throw <xref:System.NullReferenceException>, <xref:System.AccessViolationException>, nebo <xref:System.IndexOutOfRangeException>. Tyto výjimky jsou vyhrazeny a vyvolány spouštěcím modulem a ve většině případů značí chybu.  
  
 Udělejte kontrolu argumentů, aby nedocházelo k vyvolání těchto výjimek. Vyvolávání těchto výjimek zpřístupňuje podrobnosti o implementaci vaší metody, která se může v průběhu času měnit.  
  
## <a name="stackoverflowexception"></a>StackOverflowException  
 **X DO NOT** explicitní generování <xref:System.StackOverflowException>. Výjimka by měla být explicitně vyvolána pouze modulem CLR.  
  
 **X DO NOT** catch `StackOverflowException`.  
  
 Není skoro možné psát spravovaný kód, který zůstává konzistentní v přítomnosti libovolného přetečení zásobníku. Nespravované části CLR zůstávají konzistentní pomocí sond pro přesun přetečení zásobníku do dobře definovaných míst a nikoli z přetečení z libovolného zásobníku.  
  
## <a name="outofmemoryexception"></a>OutOfMemoryException  
 **X DO NOT** explicitní generování <xref:System.OutOfMemoryException>. Tato výjimka má být vyvolána pouze infrastrukturou CLR.  
  
## <a name="comexception-sehexception-and-executionengineexception"></a>ComException, SEHException – a ExecutionEngineException  
 **X DO NOT** explicitní generování <xref:System.Runtime.InteropServices.COMException>, <xref:System.ExecutionEngineException>, a <xref:System.Runtime.InteropServices.SEHException>. Tyto výjimky mají být vyvolány pouze infrastrukturou CLR.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
- [Pokyny k návrhu pro výjimky](../../../docs/standard/design-guidelines/exceptions.md)
