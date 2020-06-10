---
title: Použití standardních typů výjimek
description: Přečtěte si o standardních typech výjimek v rozhraní .NET. Přečtěte si o SystemException, ApplicationException, ArgumentException, ComException a dalších.
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- throwing exceptions, standard types
- catching exceptions
- exceptions, catching
- exceptions, throwing
ms.assetid: ab22ce03-78f9-4dca-8824-c7ed3bdccc27
ms.openlocfilehash: f95529eabd87d9ec7c379b9f790e039e1192ac53
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/10/2020
ms.locfileid: "84663054"
---
# <a name="using-standard-exception-types"></a>Použití standardních typů výjimek
Tato část popisuje standardní výjimky poskytované rozhraním a podrobnosti o jejich použití. Seznam není úplným způsobem vyčerpávající. Informace o použití jiných typů výjimek rozhraní naleznete v referenční dokumentaci k .NET Framework.

## <a name="exception-and-systemexception"></a>Výjimka a SystemException
 ❌Nevolejte <xref:System.Exception?displayProperty=nameWithType> nebo <xref:System.SystemException?displayProperty=nameWithType> .

 ❌Nepoužívejte zachycení `System.Exception` nebo `System.SystemException` v kódu architektury, pokud nechcete znovu vyvolat.

 ❌Vyhněte se zachytávání `System.Exception` nebo `System.SystemException` , s výjimkou obslužných rutin výjimek nejvyšší úrovně.

## <a name="applicationexception"></a>ApplicationException
 ❌Negenerovat nebo odvozovat z <xref:System.ApplicationException> .

## <a name="invalidoperationexception"></a>InvalidOperationException
 ✔️ vyvolat, <xref:System.InvalidOperationException> Pokud je objekt v nevhodném stavu.

## <a name="argumentexception-argumentnullexception-and-argumentoutofrangeexception"></a>ArgumentException, ArgumentNullException a ArgumentOutOfRangeException
 ✔️ throw <xref:System.ArgumentException> nebo jedno z jeho podtypů, pokud jsou do člena předány chybné argumenty. Preferovat největší odvozený typ výjimky, je-li k dispozici.

 ✔️ Nastavte `ParamName` vlastnost při vyvolání jedné z podtříd třídy `ArgumentException` .

 Tato vlastnost představuje název parametru, který způsobil výjimku vyvolání výjimky. Všimněte si, že vlastnost může být nastavena pomocí jednoho z přetížení konstruktoru.

 ✔️ použít `value` pro název parametru implicitní hodnoty pro nastavení vlastností.

## <a name="nullreferenceexception-indexoutofrangeexception-and-accessviolationexception"></a>NullReferenceException, IndexOutOfRangeException a AccessViolationException –
 ❌Nepovolujte veřejně vyvolávatná rozhraní API pro explicitní nebo implicitní vyvolání <xref:System.NullReferenceException> , <xref:System.AccessViolationException> nebo <xref:System.IndexOutOfRangeException> . Tyto výjimky jsou vyhrazeny a vyvolány spouštěcím modulem a ve většině případů značí chybu.

 Udělejte kontrolu argumentů, aby nedocházelo k vyvolání těchto výjimek. Vyvolávání těchto výjimek zpřístupňuje podrobnosti o implementaci vaší metody, která se může v průběhu času měnit.

## <a name="stackoverflowexception"></a>StackOverflowException
 ❌Nevolejte explicitně <xref:System.StackOverflowException> . Výjimka by měla být explicitně vyvolána pouze modulem CLR.

 ❌Nezachytit `StackOverflowException` .

 Není skoro možné psát spravovaný kód, který zůstává konzistentní v přítomnosti libovolného přetečení zásobníku. Nespravované části CLR zůstávají konzistentní pomocí sond pro přesun přetečení zásobníku do dobře definovaných míst a nikoli z přetečení z libovolného zásobníku.

## <a name="outofmemoryexception"></a>OutOfMemoryException
 ❌Nevolejte explicitně <xref:System.OutOfMemoryException> . Tato výjimka má být vyvolána pouze infrastrukturou CLR.

## <a name="comexception-sehexception-and-executionengineexception"></a>ComException, SEHException – a ExecutionEngineException
 ❌Nevolejte explicitně <xref:System.Runtime.InteropServices.COMException> , <xref:System.ExecutionEngineException> a <xref:System.Runtime.InteropServices.SEHException> . Tyto výjimky mají být vyvolány pouze infrastrukturou CLR.

 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*

 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*

## <a name="see-also"></a>Viz také

- [Pokyny k návrhu architektury](index.md)
- [Pokyny k návrhu pro výjimky](exceptions.md)
