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
ms.openlocfilehash: e186228d1dc9a42ddfe92428f7dfad29a5789095
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181396"
---
# <a name="how-to-map-hresults-and-exceptions"></a>Postupy: Mapování výsledků HRESULT a výjimek
Metody modelu COM hlásí chyby vrácením hodnoty HRESULTs; metody rozhraní .NET hlásí je vyvoláním výjimek. Modul runtime zpracovává přechod mezi dvěma. Každá třída výjimky v .NET Framework se mapuje na HRESULT.  
  
 Uživatelsky definované třídy výjimek mohou určovat, jaké hodnoty HRESULT jsou vhodné. Tyto třídy výjimek mohou dynamicky změnit hodnotu HRESULT, která má být vrácena při vygenerování výjimky nastavením pole **HRESULT** objektu Exception. Další informace o výjimce jsou k dispozici klientovi prostřednictvím rozhraní **IErrorInfo** , které je implementováno na objektu .NET v nespravovaném procesu.  
  
 Pokud vytvoříte třídu, která rozšiřuje **System. Exception**, je nutné nastavit pole HRESULT během konstrukce. V opačném případě základní třída přiřadí hodnotu HRESULT. Nové třídy výjimek lze namapovat na existující hodnotu HRESULT tím, že zadáte hodnotu v konstruktoru výjimky.  
  
 Všimněte si, že modul runtime někdy ignoruje `HRESULT` v případech, kde se `IErrorInfo` nachází ve vlákně.  K tomuto chování může dojít v případech, `HRESULT` kdy a `IErrorInfo` nepředstavuje stejnou chybu.  
  
### <a name="to-create-a-new-exception-class-and-map-it-to-an-hresult"></a>Chcete-li vytvořit novou třídu výjimky a namapovat ji na HRESULT  
  
1. Pomocí následujícího kódu vytvořte novou třídu výjimky `NoAccessException` a namapujte ji na HRESULT. `E_ACCESSDENIED`  
  
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
  
 Může dojít k programu (v jakémkoli programovacím jazyce), který používá spravovaný i nespravovaný kód současně. Například vlastní zařazování v následujícím příkladu kódu používá metodu **Marshal. ThrowExceptionForHR (int HRESULT)** k vyvolání výjimky s konkrétní hodnotou HRESULT. Metoda vyhledá HRESULT a vygeneruje vhodný typ výjimky. Například HRESULT v následujícím fragmentu kódu generuje **ArgumentException**.  
  
```cpp  
CMyClass::MethodThatThrows  
{  
    Marshal.ThrowExceptionForHR(COR_E_ARGUMENT);  
}  
```  
  
 Následující tabulka poskytuje úplné mapování z každého HRESULT na jeho srovnatelnou třídu výjimek v .NET Framework.  
  
|HRESULT|Výjimka .NET|  
|-------------|--------------------|  
|**MSEE_E_APPDOMAINUNLOADED**|**AppDomainUnloadedException –**|  
|**COR_E_APPLICATION**|**ApplicationException**|  
|**COR_E_ARGUMENT nebo E_INVALIDARG**|**ArgumentException**|  
|**COR_E_ARGUMENTOUTOFRANGE**|**ArgumentOutOfRangeException**|  
|**COR_E_ARITHMETIC nebo ERROR_ARITHMETIC_OVERFLOW**|**ArithmeticException –**|  
|**COR_E_ARRAYTYPEMISMATCH**|**ArrayTypeMismatchException**|  
|**COR_E_BADIMAGEFORMAT nebo ERROR_BAD_FORMAT**|**BadImageFormatException**|  
|**COR_E_COMEMULATE_ERROR**|**COMEmulateException**|  
|**COR_E_CONTEXTMARSHAL**|**ContextMarshalException**|  
|**COR_E_CORE**|**CoreException**|  
|**NTE_FAIL**|**CryptographicException –**|  
|**COR_E_DIRECTORYNOTFOUND nebo ERROR_PATH_NOT_FOUND**|**DirectoryNotFoundException**|  
|**COR_E_DIVIDEBYZERO**|**DivideByZeroException**|  
|**COR_E_DUPLICATEWAITOBJECT**|**DuplicateWaitObjectException**|  
|**COR_E_ENDOFSTREAM**|**EndOfStreamException**|  
|**COR_E_TYPELOAD**|**EntryPointNotFoundException –**|  
|**COR_E_EXCEPTION**|**Výjimka**|  
|**COR_E_EXECUTIONENGINE**|**ExecutionEngineException**|  
|**COR_E_FIELDACCESS**|**FieldAccessException**|  
|**COR_E_FILENOTFOUND nebo ERROR_FILE_NOT_FOUND**|**FileNotFoundException**|  
|**COR_E_FORMAT**|**Chyb**|  
|**COR_E_INDEXOUTOFRANGE**|**IndexOutOfRangeException**|  
|**COR_E_INVALIDCAST nebo E_NOINTERFACE**|**InvalidCastException**|  
|**COR_E_INVALIDCOMOBJECT**|**InvalidComObjectException –**|  
|**COR_E_INVALIDFILTERCRITERIA**|**InvalidFilterCriteriaException –**|  
|**COR_E_INVALIDOLEVARIANTTYPE**|**InvalidOleVariantTypeException –**|  
|**COR_E_INVALIDOPERATION**|**InvalidOperationException**|  
|**COR_E_IO**|**IOException**|  
|**COR_E_MEMBERACCESS**|**AccessException**|  
|**COR_E_METHODACCESS**|**MethodAccessException**|  
|**COR_E_MISSINGFIELD**|**MissingFieldException**|  
|**COR_E_MISSINGMANIFESTRESOURCE**|**MissingManifestResourceException**|  
|**COR_E_MISSINGMEMBER**|**MissingMemberException**|  
|**COR_E_MISSINGMETHOD**|**MissingMethodException**|  
|**COR_E_MULTICASTNOTSUPPORTED**|**MulticastNotSupportedException –**|  
|**COR_E_NOTFINITENUMBER**|**NotFiniteNumberException –**|  
|**E_NOTIMPL**|**NotImplementedException**|  
|**COR_E_NOTSUPPORTED**|**NotSupportedException**|  
|**COR_E_NULLREFERENCE orE_POINTER**|**NullReferenceException**|  
|**COR_E_OUTOFMEMORY nebo**<br /><br /> **E_OUTOFMEMORY**|**OutOfMemoryException**|  
|**COR_E_OVERFLOW**|**OverflowException**|  
|**COR_E_PATHTOOLONG nebo ERROR_FILENAME_EXCED_RANGE**|**PathTooLongException**|  
|**COR_E_RANK**|**RankException**|  
|**COR_E_REFLECTIONTYPELOAD**|**ReflectionTypeLoadException**|  
|**COR_E_REMOTING**|**RemotingException –**|  
|**COR_E_SAFEARRAYTYPEMISMATCH**|**SafeArrayTypeMismatchException –**|  
|**COR_E_SECURITY**|**SecurityException**|  
|**COR_E_SERIALIZATION**|**SerializationException**|  
|**COR_E_STACKOVERFLOW orERROR_STACK_OVERFLOW**|**StackOverflowException**|  
|**COR_E_SYNCHRONIZATIONLOCK**|**SynchronizationLockException –**|  
|**COR_E_SYSTEM**|**SystemException**|  
|**COR_E_TARGET**|**TargetException –**|  
|**COR_E_TARGETINVOCATION**|**TargetInvocationException**|  
|**COR_E_TARGETPARAMCOUNT**|**TargetParameterCountException –**|  
|**COR_E_THREADABORTED**|**ThreadAbortException**|  
|**COR_E_THREADINTERRUPTED**|**ThreadInterruptedException –**|  
|**COR_E_THREADSTATE**|**ThreadStateException –**|  
|**COR_E_THREADSTOP**|**ThreadStopException**|  
|**COR_E_TYPELOAD**|**TypeLoadException**|  
|**COR_E_TYPEINITIALIZATION**|**TypeInitializationException**|  
|**COR_E_VERIFICATION**|**VerificationException**|  
|**COR_E_WEAKREFERENCE**|**WeakReferenceException**|  
|**COR_E_VTABLECALLSNOTSUPPORTED**|**VTableCallsNotSupportedException**|  
|**Všechny ostatní HRESULTs**|**COMException**|  
  
 Chcete-li načíst rozšířené informace o chybě, musí spravovaný klient kontrolovat pole objektu výjimky, který byl vygenerován. Aby objekt objektu Exception poskytoval užitečné informace o chybě, objekt COM musí implementovat rozhraní **IErrorInfo** . Modul runtime používá informace, které poskytuje **IErrorInfo** k inicializaci objektu výjimky.  
  
 Pokud objekt modelu COM nepodporuje **IErrorInfo**, modul runtime inicializuje objekt výjimky s výchozími hodnotami. V následující tabulce jsou uvedena jednotlivá pole přidružená k objektu výjimky a určuje zdroj výchozích informací, když objekt COM podporuje **IErrorInfo**.  
  
 Všimněte si, že modul runtime někdy ignoruje `HRESULT` v případech, kde se `IErrorInfo` nachází ve vlákně.  K tomuto chování může dojít v případech, `HRESULT` kdy a `IErrorInfo` nepředstavuje stejnou chybu.  
  
|Pole výjimky|Zdroj informací z modelu COM|  
|---------------------|------------------------------------|  
|**ErrorCode**|Volání HRESULT vrátilo.|  
|**HelpLink**|Pokud **IErrorInfo->atribut HelpContext** je nenulová, je řetězec vytvořen zřetězením **IErrorInfo->GetHelpFile** a "#" a **IErrorInfo->GetHelpContext**. V opačném případě se řetězec vrátí z **IErrorInfo->GetHelpFile**.|  
|**Vnitřní**|Vždy nulový odkaz (**Nothing** v Visual Basic).|  
|**Zpráva**|Řetězec vrácený z **IErrorInfo->GetDescription**.|  
|**Zdroj**|Řetězec vrácený z **IErrorInfo->GetSource**|  
|**Trasování zásobníku**|Trasování zásobníku.|  
|**TargetSite**|Název metody, která vrátila selhání HRESULT.|  
  
 Pole výjimek, jako je například **zpráva**, **zdroj**a **trasování zásobníku** , nejsou pro **StackOverflowException**k dispozici.  
  
## <a name="see-also"></a>Viz také

- [Pokročilá interoperabilita modelu COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))
- [Výjimky](../../standard/exceptions/index.md)
