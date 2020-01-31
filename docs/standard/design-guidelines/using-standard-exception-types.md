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
ms.openlocfilehash: 3caa94d9a39966614161e4b19201dcf6065776a2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743539"
---
# <a name="using-standard-exception-types"></a>Použití standardních typů výjimek
Tato část popisuje standardní výjimky poskytované rozhraním a podrobnosti o jejich použití. Seznam není úplným způsobem vyčerpávající. Informace o použití jiných typů výjimek rozhraní naleznete v referenční dokumentaci k .NET Framework.

## <a name="exception-and-systemexception"></a>Výjimka a SystemException
 ❌ nevyvolávat <xref:System.Exception?displayProperty=nameWithType> nebo <xref:System.SystemException?displayProperty=nameWithType>.

 ❌ nezachytí `System.Exception` nebo `System.SystemException` v kódu rozhraní, pokud se nechcete znovu vyvolat.

 ❌ zabránit zachycení `System.Exception` nebo `System.SystemException`, s výjimkou obslužných rutin výjimek nejvyšší úrovně.

## <a name="applicationexception"></a>ApplicationException
 ❌ nevyvolávat nebo odvozovat z <xref:System.ApplicationException>.

## <a name="invalidoperationexception"></a>InvalidOperationException
 ✔️ vyvolat <xref:System.InvalidOperationException>, pokud je objekt v nevhodném stavu.

## <a name="argumentexception-argumentnullexception-and-argumentoutofrangeexception"></a>ArgumentException, ArgumentNullException a ArgumentOutOfRangeException
 ✔️ Vyvolejte <xref:System.ArgumentException> nebo jeden z jeho podtypů, pokud jsou do člena předány chybné argumenty. Preferovat největší odvozený typ výjimky, je-li k dispozici.

 ✔️ nastavit vlastnost `ParamName` při vyvolání jedné z podtříd `ArgumentException`.

 Tato vlastnost představuje název parametru, který způsobil výjimku vyvolání výjimky. Všimněte si, že vlastnost může být nastavena pomocí jednoho z přetížení konstruktoru.

 ✔️ použít `value` pro název parametru implicitní hodnoty vlastností Setters.

## <a name="nullreferenceexception-indexoutofrangeexception-and-accessviolationexception"></a>NullReferenceException, IndexOutOfRangeException a AccessViolationException –
 ❌ neumožňují veřejně vyvolávat rozhraní API explicitně nebo implicitně volat <xref:System.NullReferenceException>, <xref:System.AccessViolationException>nebo <xref:System.IndexOutOfRangeException>. Tyto výjimky jsou vyhrazeny a vyvolány spouštěcím modulem a ve většině případů značí chybu.

 Udělejte kontrolu argumentů, aby nedocházelo k vyvolání těchto výjimek. Vyvolávání těchto výjimek zpřístupňuje podrobnosti o implementaci vaší metody, která se může v průběhu času měnit.

## <a name="stackoverflowexception"></a>StackOverflowException
 ❌ explicitně negenerovat <xref:System.StackOverflowException>. Výjimka by měla být explicitně vyvolána pouze modulem CLR.

 ❌ nezachytit `StackOverflowException`.

 Není skoro možné psát spravovaný kód, který zůstává konzistentní v přítomnosti libovolného přetečení zásobníku. Nespravované části CLR zůstávají konzistentní pomocí sond pro přesun přetečení zásobníku do dobře definovaných míst a nikoli z přetečení z libovolného zásobníku.

## <a name="outofmemoryexception"></a>OutOfMemoryException
 ❌ explicitně negenerovat <xref:System.OutOfMemoryException>. Tato výjimka má být vyvolána pouze infrastrukturou CLR.

## <a name="comexception-sehexception-and-executionengineexception"></a>ComException, SEHException – a ExecutionEngineException
 ❌ explicitně Nevolejte <xref:System.Runtime.InteropServices.COMException>, <xref:System.ExecutionEngineException>a <xref:System.Runtime.InteropServices.SEHException>. Tyto výjimky mají být vyvolány pouze infrastrukturou CLR.

 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*

 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*

## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
- [Pokyny k návrhu pro výjimky](../../../docs/standard/design-guidelines/exceptions.md)
