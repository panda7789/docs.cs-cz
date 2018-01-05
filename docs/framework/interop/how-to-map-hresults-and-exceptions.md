---
title: "Postupy: Mapování výsledků HRESULT a výjimek"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
helpviewer_keywords:
- interoperation with unmanaged code, HRESULTs
- exceptions, HRESULTs
- interoperation with unmanaged code, exceptions
- HRESULTs
- COM interop, HRESULTs
- COM interop, exceptions
ms.assetid: 610b364b-2761-429d-9c4a-afbc3e66f1b9
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6b2c19e6076be6364f6a14159a5376a0c8c45731
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-map-hresults-and-exceptions"></a>Postupy: Mapování výsledků HRESULT a výjimek
Metody modelu COM zprávy o chybách vrácením hodnoty HRESULT; metod rozhraní .NET je sestavy vyvoláním výjimek. Modul runtime zpracovává přechod mezi nimi. Každá třída výjimky v rozhraní .NET Framework mapuje HRESULT.  
  
 Uživatelem definované výjimky třídy můžete zadat jakékoli HRESULT je vhodné. Tyto třídy výjimek, můžete změnit dynamicky HRESULT má být vrácen, když se vygeneruje výjimka nastavením **HResult** na objekt výjimky. Další informace o výjimce naleznete klientovi prostřednictvím **IErrorInfo** rozhraní, které je implementované v rozhraní .NET objektu v nespravované procesu.  
  
 Pokud vytvoříte třídu, která rozšiřuje **System.Exception**, je nutné nastavit pole HRESULT během vytváření. Základní třída přiřadí, jinak hodnota HRESULT. Můžete namapovat nové třídy výjimek na existující HRESULT zadáním hodnoty v konstruktoru v výjimky.  
  
 Všimněte si, že v některých případech bude ignorovat modulu runtime `HRESULT` v případech níž se nachází `IErrorInfo` na vlákno.  K tomuto chování dochází v případech, kde `HRESULT` a `IErrorInfo` nepředstavují ke stejné chybě.  
  
### <a name="to-create-a-new-exception-class-and-map-it-to-an-hresult"></a>Vytvořte novou třídu výjimky a namapovat je HRESULT  
  
1.  Použít následující kód k vytvoření novou třídu výjimky s názvem `NoAccessException` a namapovat je HRESULT `E_ACCESSDENIED`.  
  
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
  
 Může dojít k programu (v žádný programovací jazyk), který používá spravovaných i nespravovaných kódu ve stejnou dobu. Například používá vlastní zařazování vláken v následujícím příkladu kódu **Marshal.ThrowExceptionForHR (int HResult)** metoda k vyvolání výjimky s konkrétní hodnotou HRESULT. Metoda vyhledá hodnota HRESULT a generuje typ příslušné výjimky. Například HRESULT v následující fragment kódu vygeneruje **ArgumentException –**.  
  
```cpp  
CMyClass::MethodThatThrows  
{  
    Marshal.ThrowExceptionForHR(COR_E_ARGUMENT);  
}  
```  
  
 Následující tabulka obsahuje úplný mapování z každé HRESULT do své třídy porovnatelný z hlediska výjimek v rozhraní .NET Framework.  
  
|HRESULT|Výjimky rozhraní .NET|  
|-------------|--------------------|  
|**MSEE_E_APPDOMAINUNLOADED**|**Appdomainunloadedexception –**|  
|**COR_E_APPLICATION**|**ApplicationException –**|  
|**COR_E_ARGUMENT nebo E_INVALIDARG**|**ArgumentException –**|  
|**COR_E_ARGUMENTOUTOFRANGE**|**Výjimka ArgumentOutOfRangeException**|  
|**COR_E_ARITHMETIC nebo ERROR_ARITHMETIC_OVERFLOW**|**Arithmeticexception –**|  
|**COR_E_ARRAYTYPEMISMATCH**|**ArrayTypeMismatchException**|  
|**COR_E_BADIMAGEFORMAT nebo ERROR_BAD_FORMAT**|**BadImageFormatException**|  
|**COR_E_COMEMULATE_ERROR**|**COMEmulateException**|  
|**COR_E_CONTEXTMARSHAL**|**ContextMarshalException**|  
|**COR_E_CORE**|**CoreException**|  
|**NTE_FAIL**|**Cryptographicexception –**|  
|**COR_E_DIRECTORYNOTFOUND nebo ERROR_PATH_NOT_FOUND**|**DirectoryNotFoundException**|  
|**COR_E_DIVIDEBYZERO**|**DivideByZeroException**|  
|**COR_E_DUPLICATEWAITOBJECT**|**DuplicateWaitObjectException**|  
|**COR_E_ENDOFSTREAM**|**EndOfStreamException**|  
|**COR_E_TYPELOAD**|**Entrypointnotfoundexception –**|  
|**COR_E_EXCEPTION**|**Výjimka**|  
|**COR_E_EXECUTIONENGINE**|**ExecutionEngineException –**|  
|**COR_E_FIELDACCESS**|**FieldAccessException**|  
|**COR_E_FILENOTFOUND nebo ERROR_FILE_NOT_FOUND**|**FileNotFoundException**|  
|**COR_E_FORMAT**|**FormatException**|  
|**COR_E_INDEXOUTOFRANGE**|**IndexOutOfRangeException**|  
|**COR_E_INVALIDCAST nebo E_NOINTERFACE**|**InvalidCastException**|  
|**COR_E_INVALIDCOMOBJECT**|**InvalidComObjectException –**|  
|**COR_E_INVALIDFILTERCRITERIA**|**Invalidfiltercriteriaexception –**|  
|**COR_E_INVALIDOLEVARIANTTYPE**|**Invalidolevarianttypeexception –**|  
|**COR_E_INVALIDOPERATION**|**InvalidOperationException**|  
|**COR_E_IO**|**Výjimka vstupu/výstupu**|  
|**COR_E_MEMBERACCESS**|**AccessException**|  
|**COR_E_METHODACCESS**|**Výjimku MethodAccessException**|  
|**COR_E_MISSINGFIELD**|**MissingFieldException**|  
|**COR_E_MISSINGMANIFESTRESOURCE**|**Missingmanifestresourceexception –**|  
|**COR_E_MISSINGMEMBER**|**MissingMemberException**|  
|**COR_E_MISSINGMETHOD**|**MissingMethodException**|  
|**COR_E_MULTICASTNOTSUPPORTED**|**Multicastnotsupportedexception –**|  
|**COR_E_NOTFINITENUMBER**|**Notfinitenumberexception –**|  
|**E_NOTIMPL**|**NotImplementedException –**|  
|**COR_E_NOTSUPPORTED**|**NotSupportedException**|  
|**COR_E_NULLREFERENCE orE_POINTER**|**NullReferenceException**|  
|**COR_E_OUTOFMEMORY nebo**<br /><br /> **E_OUTOFMEMORY**|**OutOfMemoryException**|  
|**COR_E_OVERFLOW**|**OverflowException**|  
|**COR_E_PATHTOOLONG nebo ERROR_FILENAME_EXCED_RANGE**|**PathTooLongException**|  
|**COR_E_RANK**|**RankException**|  
|**COR_E_REFLECTIONTYPELOAD**|**Reflectiontypeloadexception –**|  
|**COR_E_REMOTING**|**Remotingexception –**|  
|**COR_E_SAFEARRAYTYPEMISMATCH**|**Safearraytypemismatchexception –**|  
|**COR_E_SECURITY**|**Výjimka zabezpečení**|  
|**COR_E_SERIALIZATION**|**Serializationexception –**|  
|**COR_E_STACKOVERFLOW orERROR_STACK_OVERFLOW**|**StackOverflowException**|  
|**COR_E_SYNCHRONIZATIONLOCK**|**Synchronizationlockexception –**|  
|**COR_E_SYSTEM**|**SystemException –**|  
|**COR_E_TARGET**|**Targetexception –**|  
|**COR_E_TARGETINVOCATION**|**Targetinvocationexception –**|  
|**COR_E_TARGETPARAMCOUNT**|**Targetparametercountexception –**|  
|**COR_E_THREADABORTED**|**Výjimka ThreadAbortException**|  
|**COR_E_THREADINTERRUPTED**|**Threadinterruptedexception –**|  
|**COR_E_THREADSTATE**|**Threadstateexception –**|  
|**COR_E_THREADSTOP**|**ThreadStopException**|  
|**COR_E_TYPELOAD**|**TypeLoadException –**|  
|**COR_E_TYPEINITIALIZATION**|**Typeinitializationexception –**|  
|**COR_E_VERIFICATION**|**VerificationException**|  
|**COR_E_WEAKREFERENCE**|**WeakReferenceException**|  
|**COR_E_VTABLECALLSNOTSUPPORTED**|**VTableCallsNotSupportedException**|  
|**Všechny ostatní hodnoty HRESULT**|**COMException**|  
  
 Načtení rozšířené informace o chybě, musíte klienta spravovaného prozkoumat pole objekt výjimky, která byla vygenerována. Pro objekt výjimky k poskytují užitečné informace o chybě, musí implementovat objekt COM **IErrorInfo** rozhraní. Modul runtime používá poskytnuté informace o **IErrorInfo** inicializovat objekt výjimky.  
  
 Pokud objekt COM nepodporuje **IErrorInfo**, modul runtime inicializuje objekt výjimky s výchozími hodnotami. Následující tabulka obsahuje seznam všech polí přidružená k objektu výjimky a identifikuje zdroj výchozí informace o Pokud objekt COM podporuje **IErrorInfo**.  
  
 Všimněte si, že v některých případech bude ignorovat modulu runtime `HRESULT` v případech níž se nachází `IErrorInfo` na vlákno.  K tomuto chování dochází v případech, kde `HRESULT` a `IErrorInfo` nepředstavují ke stejné chybě.  
  
|Výjimka pole|Zdroj informací z modelu COM|  
|---------------------|------------------------------------|  
|**Kód chyby**|HRESULT vrácená z volání.|  
|**HelpLink**|Pokud **IErrorInfo -> HelpContext –** je nenulové hodnoty, je tvořena řetězec zřetězením **IErrorInfo -> GetHelpFile** a "#" a **IErrorInfo -> GetHelpContext**. Jinak bude vrácen řetězec z **IErrorInfo -> GetHelpFile**.|  
|**Ve vlastnosti InnerException**|Vždy odkaz s hodnotou null (**nic** v jazyce Visual Basic).|  
|**Zpráva**|Řetězec vrácený z **IErrorInfo -> GetDescription**.|  
|**Zdroj**|Řetězec vrácený z **IErrorInfo -> GetSource**.|  
|**Trasování zásobníku**|Trasování zásobníku.|  
|**TargetSite**|Název metody, která vrátila selhání HRESULT.|  
  
 Výjimka pole, jako například **zpráva**, **zdroj**, a **trasování zásobníku** nejsou k dispozici pro **StackOverflowException**.  
  
## <a name="see-also"></a>Viz také  
 [Interoperabilita modelů COM Upřesnit](http://msdn.microsoft.com/en-us/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 [Výjimky](../../../docs/standard/exceptions/index.md)
