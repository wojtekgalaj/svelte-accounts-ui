<script>
  // import { Accounts } from "meteor/accounts-base";
  // import { Meteor } from "meteor/meteor";
  import { error } from "./state";

  export let heading = "Login";

  let email = "";
  let password = "";

  function onSubmit() {
    Meteor.loginWithPassword(email, password, err => {
      if (!err) {
        isSent = true;
        email = "";
        return;
      }
      error.set(err.reason);
    });
  }
</script>

<h3>{heading}</h3>

<form on:submit|preventDefault={onSubmit}>
  <div>
    <label>
      Email
      <input placeholder="test@yo.com" type="email" bind:value={email} />
    </label>
  </div>
  <div>
    <label>
      Password
      <input placeholder="1234" type="password" bind:value={password} />
    </label>
  </div>
  <button>Login</button>
</form>
