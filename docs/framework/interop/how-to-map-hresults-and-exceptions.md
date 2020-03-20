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
Metody COM hlásí chyby vrácením HRESULTs; .NET metody sestavy je vyvoláním výjimek. Runtime zpracovává přechod mezi těmito dvěma. Každá třída výjimky v rozhraní .NET Framework se mapuje na HRESULT.  
  
 Uživatelem definované třídy výjimek můžete určit, co HRESULT je vhodné. Tyto třídy výjimek mohou dynamicky změnit HRESULT, který má být vrácen, když je generována výjimka nastavením pole **HResult** na objektu výjimky. Další informace o výjimce jsou klientovi poskytovány prostřednictvím rozhraní **IErrorInfo,** které je implementováno na objektu .NET v nespravovaném procesu.  
  
 Pokud vytvoříte třídu, která rozšiřuje **System.Exception**, musíte nastavit pole HRESULT během výstavby. V opačném případě základní třída přiřadí hodnotu HRESULT. Můžete mapovat nové třídy výjimek na existující HRESULT zadáním hodnoty v konstruktoru výjimky.  
  
 Všimněte si, že runtime bude někdy ignorovat `HRESULT` v případech, kdy je `IErrorInfo` přítomen ve vlákně.  K tomuto chování může `HRESULT` dojít `IErrorInfo` v případech, kdy a nepředstavují stejnou chybu.  
  
### <a name="to-create-a-new-exception-class-and-map-it-to-an-hresult"></a>Chcete-li vytvořit novou třídu výjimek a namapovat ji na HRESULT  
  
1. Pomocí následujícího kódu vytvořte novou `NoAccessException` třídu výjimek `E_ACCESSDENIED`s názvem a namapujte ji na HRESULT .  
  
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
  
 Může dojít k programu (v libovolném programovacím jazyce), který používá spravovaný i nespravovaný kód současně. Například vlastní zařazování v následujícím příkladu kódu používá **metodu Marshal.ThrowExceptionForHR(int HResult)** k vyvolání výjimky s konkrétní hodnotou HRESULT. Metoda vyhledá HRESULT a vygeneruje příslušný typ výjimky. Například HRESULT v následujícím fragmentu kódu generuje **ArgumentException**.  
  
```cpp  
CMyClass::MethodThatThrows  
{  
    Marshal.ThrowExceptionForHR(COR_E_ARGUMENT);  
}  
```  
  
 Následující tabulka obsahuje úplné mapování z každého HRESULT na jeho srovnatelnou třídu výjimek v rozhraní .NET Framework.  
  
|HRESULT|Výjimka .NET|  
|-------------|--------------------|  
|**MSEE_E_APPDOMAINUNLOADED**|**AppDomainUnloadedException**|  
|**COR_E_APPLICATION**|**Applicationexception**|  
|**COR_E_ARGUMENT nebo E_INVALIDARG**|**Argumentexception**|  
|**COR_E_ARGUMENTOUTOFRANGE**|**ArgumentOutOfRangeException**|  
|**COR_E_ARITHMETIC nebo ERROR_ARITHMETIC_OVERFLOW**|**Arithmeticexception**|  
|**COR_E_ARRAYTYPEMISMATCH**|**Výjimka PoleTypeMismatchException**|  
|**COR_E_BADIMAGEFORMAT nebo ERROR_BAD_FORMAT**|**Badimageformatexception**|  
|**COR_E_COMEMULATE_ERROR**|**Výjimka COMEmulateException**|  
|**COR_E_CONTEXTMARSHAL**|**ContextMarshalException**|  
|**COR_E_CORE**|**CoreException**|  
|**NTE_FAIL**|**Cryptographicexception**|  
|**COR_E_DIRECTORYNOTFOUND nebo ERROR_PATH_NOT_FOUND**|**Directorynotfoundexception**|  
|**COR_E_DIVIDEBYZERO**|**Dividebyzeroexception**|  
|**COR_E_DUPLICATEWAITOBJECT**|**Duplicatewaitobjectexception**|  
|**COR_E_ENDOFSTREAM**|**Výjimka EndOfStreamException**|  
|**COR_E_TYPELOAD**|**EntryPointNotFoundException**|  
|**COR_E_EXCEPTION**|**Výjimka**|  
|**COR_E_EXECUTIONENGINE**|**ExecutionEngineException**|  
|**COR_E_FIELDACCESS**|**FieldAccessException**|  
|**COR_E_FILENOTFOUND nebo ERROR_FILE_NOT_FOUND**|**Filenotfoundexception**|  
|**COR_E_FORMAT**|**FormatException**|  
|**COR_E_INDEXOUTOFRANGE**|**Výjimka IndexOutOfRangeException**|  
|**COR_E_INVALIDCAST nebo E_NOINTERFACE**|**Invalidcastexception**|  
|**COR_E_INVALIDCOMOBJECT**|**Neplatnýobjekt**|  
|**COR_E_INVALIDFILTERCRITERIA**|**NeplatnýfiltrickýkritériaException**|  
|**COR_E_INVALIDOLEVARIANTTYPE**|**Výjimka typu Typu Neplatnostolevariant**|  
|**COR_E_INVALIDOPERATION**|**InvalidOperationException**|  
|**COR_E_IO**|**Ioexception**|  
|**COR_E_MEMBERACCESS**|**AccessException**|  
|**COR_E_METHODACCESS**|**Exceptiona MethodAccessException**|  
|**COR_E_MISSINGFIELD**|**Chybějící výjimka pole**|  
|**COR_E_MISSINGMANIFESTRESOURCE**|**Chybějící výjimka manifestu**|  
|**COR_E_MISSINGMEMBER**|**Chybějícívýjimka člena**|  
|**COR_E_MISSINGMETHOD**|**Chybějící výjimka**|  
|**COR_E_MULTICASTNOTSUPPORTED**|**Multicastnotsupportedexception**|  
|**COR_E_NOTFINITENUMBER**|**NotFiniteNumberException**|  
|**E_NOTIMPL**|**Notimplementedexception**|  
|**COR_E_NOTSUPPORTED**|**Notsupportedexception**|  
|**COR_E_NULLREFERENCE orE_POINTER**|**Nullreferenceexception**|  
|**COR_E_OUTOFMEMORY nebo**<br /><br /> **E_OUTOFMEMORY**|**Outofmemoryexception**|  
|**COR_E_OVERFLOW**|**PřetečeníVýjimka**|  
|**COR_E_PATHTOOLONG nebo ERROR_FILENAME_EXCED_RANGE**|**Pathtoolongexception**|  
|**COR_E_RANK**|**Výjimka z ranku**|  
|**COR_E_REFLECTIONTYPELOAD**|**ReflectionTypeLoadException**|  
|**COR_E_REMOTING**|**Výjimka vzdálené komunikace**|  
|**COR_E_SAFEARRAYTYPEMISMATCH**|**Výjimka SafeArrayTypeMismatchException**|  
|**COR_E_SECURITY**|**Securityexception**|  
|**COR_E_SERIALIZATION**|**Serializationexception**|  
|**COR_E_STACKOVERFLOW orERROR_STACK_OVERFLOW**|**Stackoverflowexception**|  
|**COR_E_SYNCHRONIZATIONLOCK**|**SynconLockException**|  
|**COR_E_SYSTEM**|**Systemexception**|  
|**COR_E_TARGET**|**Cílová výjimka**|  
|**COR_E_TARGETINVOCATION**|**TargetInvocationException**|  
|**COR_E_TARGETPARAMCOUNT**|**Parametr TargetParameterCountException**|  
|**COR_E_THREADABORTED**|**Threadabortexception**|  
|**COR_E_THREADINTERRUPTED**|**ThreadInterruptedException**|  
|**COR_E_THREADSTATE**|**ThreadStateException**|  
|**COR_E_THREADSTOP**|**ThreadStopException**|  
|**COR_E_TYPELOAD**|**Typeloadexception**|  
|**COR_E_TYPEINITIALIZATION**|**TypInicializaceException**|  
|**COR_E_VERIFICATION**|**Ověřovací výjimka**|  
|**COR_E_WEAKREFERENCE**|**WeakReferenceException**|  
|**COR_E_VTABLECALLSNOTSUPPORTED**|**vtablecallsnení podporovánavýjimka**|  
|**Všechny ostatní HRESULTs**|**Comexception**|  
  
 Chcete-li načíst rozšířené informace o chybě, musí klient spravovaný zkontrolovat pole objektu výjimky, který byl vygenerován. Aby objekt výjimky poskytl užitečné informace o chybě, musí objekt COM implementovat rozhraní **IErrorInfo.** Runtime používá informace poskytnuté **IErrorInfo** k inicializaci objektu výjimky.  
  
 Pokud objekt COM nepodporuje **iErrorInfo**, runtime inicializuje objekt výjimky s výchozími hodnotami. V následující tabulce jsou uvedeny všechny pole přidružené k objektu výjimky a identifikuje zdroj výchozích informací, když objekt COM podporuje **technologii IErrorInfo**.  
  
 Všimněte si, že runtime bude někdy ignorovat `HRESULT` v případech, kdy je `IErrorInfo` přítomen ve vlákně.  K tomuto chování může `HRESULT` dojít `IErrorInfo` v případech, kdy a nepředstavují stejnou chybu.  
  
|Pole výjimky|Zdroj informací od kom.|  
|---------------------|------------------------------------|  
|**Errorcode**|HRESULT vrátil z volání.|  
|**Helplink**|Pokud je **iErrorInfo->HelpContext** nenulový, je řetězec vytvořen zřetězením **iErrorInfo->GetHelpFile** a "#" a **IErrorInfo->GetHelpContext**. V opačném případě je řetězec vrácen z **souboru GetHelpFile iErrorInfo->.**|  
|**Innerexception**|Vždy odkaz null **(Nothing** v jazyce Visual Basic).|  
|**Zprávu**|Řetězec vrácený z **aplikace IErrorInfo->GetDescription**.|  
|**Zdroj**|Řetězec vrácený z **iErrorInfo->GetSource**.|  
|**Stacktrace**|Trasování zásobníku.|  
|**Cílový web**|Název metody, která vrátila selhání HRESULT.|  
  
 Pole výjimek, například **Message**, **Source**a **StackTrace,** nejsou k dispozici pro **výjimku StackOverflowException**.  
  
## <a name="see-also"></a>Viz také

- [Pokročilá interoperabilita com](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))
- [Výjimky](../../standard/exceptions/index.md)
