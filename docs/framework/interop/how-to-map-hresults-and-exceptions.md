---
title: 'Postupy: Mapování výsledků HRESULT a výjimek'
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- interoperation with unmanaged code, HRESULTs
- exceptions, HRESULTs
- interoperation with unmanaged code, exceptions
- HRESULTs
- COM interop, HRESULTs
- COM interop, exceptions
ms.assetid: 610b364b-2761-429d-9c4a-afbc3e66f1b9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 609f7f6e5460bf315b87725405496e95abbfdd95
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59102762"
---
# <a name="how-to-map-hresults-and-exceptions"></a>Postupy: Mapování výsledků HRESULT a výjimek
Metody modelu COM zprávy o chybách tak, že vrací výsledky HRESULT; metod rozhraní .NET dejte nám o nich vyvoláním výjimky. Modul runtime zpracovává přechod mezi nimi. Každá třída výjimky v rozhraní .NET Framework se mapuje na HRESULT.  
  
 Třídy výjimek definované uživatelem můžete zadat jakékoli HRESULT je vhodné. Tyto třídy výjimek můžete dynamicky měnit hodnota HRESULT, který se má vrátit, když výjimka je vygenerován pomocí nastavení **HResult** pole objektu výjimky. Další informace o výjimce jsou uvedeny do klienta prostřednictvím **IErrorInfo** rozhraní, které je implementované u objektu rozhraní .NET v nespravovaný proces.  
  
 Pokud vytvoříte třídu, která rozšiřuje **System.Exception**, je nutné nastavit pole HRESULT během konstrukce. V opačném případě základní třídy přiřadí hodnotu HRESULT. Nové třídy výjimek můžete namapovat na stávající HRESULT zadáním hodnoty v konstruktoru pro výjimku.  
  
 Všimněte si, že modul runtime bude ignorovat někdy `HRESULT` v případech, ve kterých je `IErrorInfo` k dispozici ve vlákně.  K tomuto chování dochází v případech, kde `HRESULT` a `IErrorInfo` část nepředstavují stejnou chybu.  
  
### <a name="to-create-a-new-exception-class-and-map-it-to-an-hresult"></a>Chcete-li vytvořit novou třídu výjimky a jejich mapování na HRESULT  
  
1.  Pomocí následujícího kódu vytvořte novou třídu výjimek s názvem `NoAccessException` a jejich mapování na HRESULT `E_ACCESSDENIED`.  
  
    ```cpp  
    Class NoAccessException : public ApplicationException  
    {  
        NoAccessException () {  
        HResult = E_ACCESSDENIED;   
    }  
    }  
    CMyClass::MethodThatThrows  
    {  
    throw new NoAccessException();  
    }  
    ```  
  
 Může dojít k programu (v libovolném programovacím jazyce), který používá spravovaný a nespravovaný kód ve stejnou dobu. Například používá vlastní zařazovací modul v následujícím příkladu kódu **Marshal.ThrowExceptionForHR (int HResult)** metoda k vyvolání výjimky s konkrétní hodnotou HRESULT. Metoda vyhledá HRESULT a generuje typ příslušné výjimky. Například hodnota HRESULT v následující fragment kódu vygeneruje **ArgumentException**.  
  
```cpp  
CMyClass::MethodThatThrows  
{  
    Marshal.ThrowExceptionForHR(COR_E_ARGUMENT);  
}  
```  
  
 Následující tabulka obsahuje kompletní mapování z každé HRESULT na jeho třída srovnatelné výjimek v rozhraní .NET Framework.  
  
|HRESULT|Výjimky .NET|  
|-------------|--------------------|  
|**MSEE_E_APPDOMAINUNLOADED**|**AppDomainUnloadedException**|  
|**COR_E_APPLICATION**|**ApplicationException**|  
|**COR_E_ARGUMENT nebo E_INVALIDARG**|**ArgumentException**|  
|**COR_E_ARGUMENTOUTOFRANGE**|**ArgumentOutOfRangeException**|  
|**COR_E_ARITHMETIC nebo ERROR_ARITHMETIC_OVERFLOW**|**ArithmeticException**|  
|**COR_E_ARRAYTYPEMISMATCH**|**ArrayTypeMismatchException**|  
|**COR_E_BADIMAGEFORMAT nebo ERROR_BAD_FORMAT**|**BadImageFormatException**|  
|**COR_E_COMEMULATE_ERROR**|**COMEmulateException**|  
|**COR_E_CONTEXTMARSHAL**|**ContextMarshalException**|  
|**COR_E_CORE**|**CoreException**|  
|**NTE_FAIL**|**CryptographicException**|  
|**COR_E_DIRECTORYNOTFOUND nebo ERROR_PATH_NOT_FOUND**|**DirectoryNotFoundException**|  
|**COR_E_DIVIDEBYZERO**|**DivideByZeroException**|  
|**COR_E_DUPLICATEWAITOBJECT**|**DuplicateWaitObjectException**|  
|**COR_E_ENDOFSTREAM**|**EndOfStreamException**|  
|**COR_E_TYPELOAD**|**EntryPointNotFoundException**|  
|**COR_E_EXCEPTION**|**Výjimka**|  
|**COR_E_EXECUTIONENGINE**|**ExecutionEngineException –**|  
|**COR_E_FIELDACCESS**|**FieldAccessException**|  
|**COR_E_FILENOTFOUND nebo ERROR_FILE_NOT_FOUND**|**FileNotFoundException**|  
|**COR_E_FORMAT**|**FormatException**|  
|**COR_E_INDEXOUTOFRANGE**|**IndexOutOfRangeException**|  
|**COR_E_INVALIDCAST nebo E_NOINTERFACE**|**InvalidCastException**|  
|**COR_E_INVALIDCOMOBJECT**|**InvalidComObjectException**|  
|**COR_E_INVALIDFILTERCRITERIA**|**InvalidFilterCriteriaException**|  
|**COR_E_INVALIDOLEVARIANTTYPE**|**InvalidOleVariantTypeException**|  
|**COR_E_INVALIDOPERATION**|**InvalidOperationException**|  
|**COR_E_IO**|**IOException –**|  
|**COR_E_MEMBERACCESS**|**AccessException**|  
|**COR_E_METHODACCESS**|**MethodAccessException**|  
|**COR_E_MISSINGFIELD**|**MissingFieldException**|  
|**COR_E_MISSINGMANIFESTRESOURCE**|**MissingManifestResourceException**|  
|**COR_E_MISSINGMEMBER**|**MissingMemberException**|  
|**COR_E_MISSINGMETHOD**|**MissingMethodException**|  
|**COR_E_MULTICASTNOTSUPPORTED**|**MulticastNotSupportedException**|  
|**COR_E_NOTFINITENUMBER**|**NotFiniteNumberException**|  
|**E_NOTIMPL**|**NotImplementedException**|  
|**COR_E_NOTSUPPORTED**|**NotSupportedException**|  
|**COR_E_NULLREFERENCE orE_POINTER**|**NullReferenceException**|  
|**COR_E_OUTOFMEMORY nebo**<br /><br /> **E_OUTOFMEMORY**|**OutOfMemoryException**|  
|**COR_E_OVERFLOW**|**OverflowException**|  
|**COR_E_PATHTOOLONG nebo ERROR_FILENAME_EXCED_RANGE**|**PathTooLongException**|  
|**COR_E_RANK**|**Rankexception –**|  
|**COR_E_REFLECTIONTYPELOAD**|**ReflectionTypeLoadException**|  
|**COR_E_REMOTING**|**Remotingexception –**|  
|**COR_E_SAFEARRAYTYPEMISMATCH**|**SafeArrayTypeMismatchException**|  
|**COR_E_SECURITY**|**SecurityException –**|  
|**COR_E_SERIALIZATION**|**SerializationException**|  
|**COR_E_STACKOVERFLOW orERROR_STACK_OVERFLOW**|**StackOverflowException**|  
|**COR_E_SYNCHRONIZATIONLOCK**|**SynchronizationLockException**|  
|**COR_E_SYSTEM**|**SystemException**|  
|**COR_E_TARGET**|**TargetException**|  
|**COR_E_TARGETINVOCATION**|**Targetinvocationexception –**|  
|**COR_E_TARGETPARAMCOUNT**|**TargetParameterCountException**|  
|**COR_E_THREADABORTED**|**ThreadAbortException**|  
|**COR_E_THREADINTERRUPTED**|**ThreadInterruptedException**|  
|**COR_E_THREADSTATE**|**ThreadStateException**|  
|**COR_E_THREADSTOP**|**ThreadStopException**|  
|**COR_E_TYPELOAD**|**TypeLoadException**|  
|**COR_E_TYPEINITIALIZATION**|**Typeinitializationexception –**|  
|**COR_E_VERIFICATION**|**Verificationexception –**|  
|**COR_E_WEAKREFERENCE**|**WeakReferenceException**|  
|**COR_E_VTABLECALLSNOTSUPPORTED**|**VTableCallsNotSupportedException**|  
|**Všechny ostatní výsledky HRESULT**|**COMException**|  
  
 Chcete-li získat rozšířené informace o chybě, musíte prozkoumat spravovaného klienta polí objekt výjimky, která byla vygenerována. Pro objekt výjimky k poskytují užitečné informace o chybě, musí implementovat objekt modelu COM **IErrorInfo** rozhraní. Modul runtime používá na základě informací poskytnutých **IErrorInfo** k inicializaci objektu výjimky.  
  
 Pokud objekt COM nepodporuje **IErrorInfo**, modul runtime inicializuje objekt výjimky s výchozími hodnotami. Následující tabulka obsahuje seznam všech polí přidružené k objektu výjimky a identifikuje zdroj informací, výchozí, když objekt modelu COM podporuje **IErrorInfo**.  
  
 Všimněte si, že modul runtime bude ignorovat někdy `HRESULT` v případech, ve kterých je `IErrorInfo` k dispozici ve vlákně.  K tomuto chování dochází v případech, kde `HRESULT` a `IErrorInfo` část nepředstavují stejnou chybu.  
  
|Pole výjimky|Zdroje informací z modelu COM|  
|---------------------|------------------------------------|  
|**Kód chyby**|HRESULT vrácená z volání.|  
|**HelpLink**|Pokud **IErrorInfo -> HelpContext** je nenulová, řetězec je vytvořený zřetězením **IErrorInfo -> GetHelpFile** a "#" a **IErrorInfo -> GetHelpContext**. V opačném případě vrátí řetězec **IErrorInfo -> GetHelpFile**.|  
|**InnerException**|Vždy odkaz s hodnotou null (**nic** v jazyce Visual Basic).|  
|**Zpráva**|Řetězec vrácený z **IErrorInfo -> GetDescription**.|  
|**Zdroj**|Řetězec vrácený z **IErrorInfo -> GetSource**.|  
|**Trasování zásobníku**|Trasování zásobníku.|  
|**TargetSite**|Název metody, která vrátí selhání HRESULT.|  
  
 Výjimka pole, jako například **zpráva**, **zdroj**, a **trasování zásobníku** nejsou k dispozici pro **StackOverflowException –**.  
  
## <a name="see-also"></a>Viz také:

- [Rozšířená interoperabilita modelu COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))
- [Výjimky](../../standard/exceptions/index.md)
