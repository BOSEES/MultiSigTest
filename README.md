처음에 말씀해주신 방법중
 1. 실행할 멀티시그 트랜잭션 내용 + 필요한 여러 개의 서명을 동시에 트랜잭션의 data 영역에 담아서 보내는 방법
 2. 일단 실행할 트랜잭션 후보를 컨트랙트에 저장하는 트랜잭션을 보내고, 멀티시그 할 사람들이 별도로 컨펌 트랜잭션을 보내 후보가 나중에 실행되게 하는 방법

 2번을 채택해서 Consensys의 멀티시그 구현체를 가져와서 쓸려고 합니다.


 하지만 현재 진행중인 프로잭트에서 Klaytn 네트워크에 사용할 기본 토큰 표준 라이브러리 KIP-7 이라는 걸 사용하게끔 얘기가 나와서 문제입니다. Klaytn 에서 제공하는 컨트렉트가 다 0.5.x버전대로 사용중이라 Multisig 버전을 0.5.x 버전으로 포팅하기로 결정했습니다.
 (물론 7버전이 아쉽지만ㅜㅜ 환경이 0.5.x버전을 쓰게끔 하네요.)

 컨트렉트는 구조는 klaymore가 저희가 쓰는 토큰 컨트랙트 이구요 Multisig는 상속받아서 사용할려고 합니다.


일단 개인적으로 한번 포팅을 0.5.x 버전대로 포팅을 해봤는데 정상적으로 한건지는 잘 모르겠네요. 컴파일까지는 정상적으로 됩니다.

가장 큰 문제는 배포시 생성자 함수에 넣을 파라매터 값을 어떻게 넣어야할지 모르겠습니다.
에러 문구는 이렇게 나옵니다.
테스트 환경은 이렇습니다.:
https://ide.klaytn.com/

    creation of MultiSigWallet errored: Error encoding arguments: Error: expected array value (arg="", coderType="array", type="string", value="")

배포시 생성자에 지갑어드레스를 넣으면 value="" 에 지갑어드레스만 들어가고 에러가 다시 뜹니다.

     creation of MultiSigWallet errored: Error encoding arguments: Error: expected array value (arg="", coderType="array", type="string", value="지갑 어드레스")